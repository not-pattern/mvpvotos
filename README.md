# AppVotos — MVP

Infraestructura de votación pagada para eventos en vivo. Prototipo navegable para mostrar a discotecas y productores, y para la postulación a Startup Chile.

> Datos ficticios y pagos simulados. No hay backend: todo corre en el navegador.

## Archivos

| Archivo | Qué es |
|---|---|
| `index.html` | Portada con acceso a las tres vistas |
| `votante.html` | Flujo del votante (móvil): ranking en grilla de 3 columnas → pack de votos → pago → repartir votos tocando perfiles → comprobante |
| `productor.html` | Panel del productor: KPIs, concursantes, reparto configurable del pozo, packs, rondas y registro auditable |
| `overlay.html` | Overlay para la transmisión: pozo en vivo, top 5, QR y último voto (con simulación de votos) |

Cada HTML es independiente: abre cualquiera con doble clic. Solo necesita internet para cargar las fuentes de Google Fonts.

## Publicarlo en GitHub Pages

1. Sube la carpeta a un repositorio.
2. En el repo: **Settings → Pages → Source: Deploy from a branch**, rama `main`, carpeta `/ (root)`.
3. Queda en `https://<tu-usuario>.github.io/<repo>/`.

## Overlay en OBS / Streamlabs

Agrega una **Fuente de navegador** con la URL de `overlay.html?obs=1` (fondo transparente), tamaño 1920×1080.

## Personalizar

Cada archivo tiene arriba del `<script>` un bloque `DATOS DE EJEMPLO`:

- **Concursantes:** nombre, iniciales, color y `photo` (URL de la foto; si está vacía se muestran las iniciales).
- **Packs:** cantidad de votos y precio.
- **Reparto:** `POT_SHARE` (% al pozo) en `votante.html`; `PLATFORM_FEE` (12% fijo) en `productor.html`.

## Supuestos del modelo

- AppVotos **no guarda dinero**: los pagos los procesa un proveedor regulado.
- Comisión de la plataforma fija en 12% (pasarela + operación). El productor define cuánto va al pozo y cuánto a la discoteca.
- El reparto se fija al publicar las bases y no cambia durante la temporada.
- Se venden **packs de votos** (bien digital consumible), no saldo retirable.

## Barreras a resolver (roadmap)

1. Billetera propia con saldo → requiere licencia de emisor de prepago (CMF / Banco Central).
2. Custodia del pozo y liberación al ganador.
3. Integridad del conteo: registro auditable, antifraude, comprobantes verificables.
4. Bases e impuestos del premio.

## Próximos pasos técnicos

- Backend con base de datos (concursos, concursantes, votos, comprobantes).
- Integración con proveedor de pagos (Mercado Pago, Flow, Khipu o Fintoc).
- Tiempo real para el overlay (websockets).
- Autenticación del productor y carga de fotos.
