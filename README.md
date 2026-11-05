# Atlas territorial del Índice de Bienestar Policial 1.0

Sitio estático listo para alojarse mediante **GitHub Pages**, con mapas interactivos sobre fondo blanco y consulta por las **26 subzonas policiales del Ecuador**. Muestra el índice global y las dimensiones D1 a D5 con sus puntuaciones descriptivas. No incluye datos personales.

## Publicación en GitHub Pages

Crea un repositorio de GitHub, por ejemplo `atlas-ibp-ecuador`, y carga en la raíz **todos** los archivos y la carpeta `datos/` que acompañan este README. En **Settings → Pages → Build and deployment**, selecciona **Deploy from a branch**, la rama `main` y la carpeta `/ (root)` y guarda. GitHub publicará una dirección del tipo `https://USUARIO.github.io/atlas-ibp-ecuador/` cuando se complete el despliegue.

También puedes abrir `index.html` directamente desde tu computador si tienes conexión a internet. La geometría se encuentra incorporada en `datos.js`, de manera que no necesita un servidor local; Leaflet se carga desde la red pública unpkg.com.

## Interacción

El menú superior permite seleccionar el índice global o las cinco dimensiones. Al hacer clic en una subzona del mapa se actualiza la ficha lateral con las seis puntuaciones. También es posible buscar por nombre, filtrar por zona, activar límites zonales, elegir entre escala de color relativa o fija y acercarse a Galápagos. El botón «Descargar datos CSV» facilita reutilizar los 26 resultados.

## Integridad de los datos

Las puntuaciones se transcribieron directamente del cuadro **3.1. Cuadro territorial completo**, en `20261104_PNE_IBP_1_0_Informe_Estadistico_Resultados_26_Subzonas.docx`. Se cotejaron los 26 nombres y las nueve zonas del informe con los campos `DPA_DESPRO`, `DPA_PROVIN` y `Zona` del archivo `subzonas.shp`. No se imputó ni recalculó ninguna puntuación de bienestar. La geometría original contenía 29 registros: se excluyeron **tres zonas no delimitadas** sin puntuaciones del índice. Se conservan los 26 territorios del informe, incluidos DMQ y DMG.

Los polígonos originales se transformaron de **WGS84 / UTM zona 17S (EPSG:32717)** a **WGS84 (EPSG:4326)** y se simplificaron para mejorar la carga del navegador. `ZONAS.zip` no contenía el archivo indispensable `.shp`, por lo cual la capa opcional de límites de las nueve zonas se obtuvo mediante disolución de las 26 subzonas, no a partir del archivo incompleto.

El archivo `datos/metadatos.json` documenta el procesamiento. `datos/subzonas_ibp_2026.geojson` incluye exclusivamente geometría, identificador geográfico, zona y seis puntuaciones, excluyendo campos sociodemográficos históricos y demás atributos del shapefile original.

## Advertencia científica

Es una **versión piloto de discusión y validación**. Las puntuaciones no son una clasificación oficial ni estimaciones representativas del bienestar de los individuos. La encuesta contiene **1.419 registros**, sin diseño probabilístico subzonal documentado. Hay proxies y valores compartidos entre determinadas jurisdicciones, y la media no está ponderada por tamaño de la fuerza policial. No deben inferirse relaciones causales ni categorías de riesgo a partir del mapa. El diseño de indicadores y sus pesos requieren validación.

## Estructura

`index.html`: interfaz. `styles.css`: identidad visual, fondo blanco y diseño responsive. `app.js`: lógica de mapa, leyendas, perfiles y filtros. `datos.js`: geodatos incorporados para ejecución sin servidor. `datos/resultados_26_subzonas.csv`: resultados numéricos. `datos/subzonas_ibp_2026.geojson`: límites simplificados. `datos/limites_zonas_derivadas.geojson`: nueve zonas reconstruidas. `datos/metadatos.json`: procedencia, restricciones y transformaciones.

## Próxima fase

Para añadir los **treinta indicadores individuales**, numeradores, denominadores, notas de auditoría, procedencia por celda y gráficos, debe incorporarse y verificarse el libro matriz `20261104_PNE_IBP_1_0_26_SUBZONAS_CON_PROXIES_AUDITADOS.xlsx`, que **no formó parte de los archivos adjuntos al generar este prototipo**. El CSV `IBP_Preguntas_Forms.csv` corresponde a la estructura de preguntas del formulario, no a las 780 celdas auditadas del índice.


## Dirección pública del atlas

Una vez completada la publicación desde la rama `main` y la carpeta `/(root)`, el sitio se consulta en https://williamsjimenez.github.io/atlas-ibp-ecuador/.
