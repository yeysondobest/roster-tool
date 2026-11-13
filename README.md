# Roster Tool — Yeyson Morrobel

Herramienta simple para manejar listas de jugadores (roster): pegar desde Word, subir un PDF,
limpiar, convertir a mayúsculas, copiar, descargar y detectar números repetidos.

Es **un solo archivo** (`index.html`): no necesita servidor, ni hoja de cálculo, ni cuenta.

## Qué hace

| Botón | Acción |
|---|---|
| **Procesar texto** | Toma lo pegado y arma las filas (nombre, número, talla, cantidad, set). |
| **Descargar Word (texto)** | Convierte lo pegado en un `.doc` que abre Word. |
| **Borrar** | Vacía la tabla y el texto. |
| **MAYÚSCULAS** | Pone en mayúsculas nombre, configuración y set. |
| **Primera Letra Mayúscula** | Capitaliza nombre y configuración. |
| **COPIAR** | Copia toda la tabla al portapapeles (TSV, se pega en Excel/Sheets). |
| **Descargar CSV** | Exporta la tabla a CSV con el nombre `SO-XXXX_Roster_AAAAMMDD_HHMMSS.csv`. |
| **Números repetidos** | Resalta filas con el mismo PlayerNumber y los lista. |
| **+ Fila** | Agrega una fila vacía para editar a mano. |

## PDF → Word y extracción

1. Arrastra un **PDF** al recuadro (o haz clic para elegirlo).
2. El texto se extrae y aparece en el cuadro grande.
3. **PDF → Word** genera un **.docx real** (Word) con el texto del PDF y, si ya procesaste el roster, también la **tabla** de jugadores.
4. Pulsa **Procesar texto** para llenar la tabla (revisa y corrige lo que haga falta).
5. Descarga los datos con **Descargar CSV** (formato para Excel/Sheets).

- Soporta varias tablas/sets en el mismo PDF: **no importa cuántos sets** traiga, se leen todos.
- La descarga de datos es siempre **CSV**; Word se usa solo para la conversión del PDF.

## Descargas y nombre del archivo

El nombre de la orden (SO) se **detecta del nombre del PDF** (ej. `SO3985522A-JMSV1-Rolling.pdf` → `SO-3985522`).
También puedes escribirlo a mano en el campo **SO** (se guarda en el navegador).

**Descargar Excel** genera un `.xlsx` igual al del reporte:

```
SO-3985522_Roster_20261113_095720.xlsx
├─ Hoja "A" → PlayerName · PlayerNumber · Year · Quantity · ProductConfiguration · ProductSize
└─ Hoja "B" → (misma estructura)
```

- Una **hoja por set** (A, B, C…). Si no hay set, todo va en la hoja `A`.
- Columnas exactas del formato: 6, sin columna "Set".
- También puedes descargar **CSV** (una sola tabla con la columna Set).

## Formato de la tabla

- **ProductConfiguration**: `YOUTH` o `ADULT`, se deduce de la talla (YS/YL/YXL → YOUTH; S/M/L/XL → ADULT).
- **ProductSize**: la talla sin la Y (YS → S, YXL → XL).
- **Quantity**: la cantidad del roster.
- Reconoce la tabla `PLAYER NAME or SPONSOR | NUMBER | SIZE | QUANTITY` del PDF/Word del roster.

## Columnas
`Playername · PlayerNumber · Year · Quantity · ProductConfiguration · ProductSize · Set`

Las tallas reconocidas son: YXXS, YXS, YS, YM, YL, YXL, AXXS, AXS, AS, AM, AL, AXL, A2XL, A3XL, A4XL,
XXS, XS, S, M, L, XL, 2XL, 3XL, 4XL, 5XL.

## Datos
Todo se guarda **solo en tu navegador** (localStorage). Nada se sube a internet.
Usa **COPIAR** o **Descargar CSV** para respaldar.

## Publicarlo (GitHub Pages)
1. Crea un repo (ej. `roster-tool`) **público** (GitHub Pages gratis).
2. Sube `index.html` a la raíz → **Commit changes**.
3. Settings → Pages → Deploy from a branch → `main` / `(root)` → Save.
4. En 1–2 min: `https://yeysondobest.github.io/roster-tool/`

No hay datos sensibles en el archivo, así que puede ser público.
