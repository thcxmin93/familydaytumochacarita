# Portfolio · Octubre 2026 — TUMO Chacarita

Página pública con los trabajos finales de los estudiantes de TUMO Chacarita (octubre 2026), organizada por disciplina.

**Página publicada:** https://familydaytumochacarita.pages.dev

## Cómo se publica

La página está conectada a **Cloudflare Pages**. Cada cambio que se guarda (commit) en la rama `main` de este repositorio se publica solo en 1–2 minutos. No hay que compilar nada: son archivos HTML, JS e imágenes estáticas.

> Ojo: todo lo que se sube a `main` queda online enseguida. Si vas a probar algo grande, mejor hacerlo en otra rama primero.

## Estructura

| Carpeta / archivo | Qué es |
| --- | --- |
| `index.html` | Inicio con las 8 disciplinas |
| `modelado.html`, `data.js`, `models/`, `renders/` | Modelado 3D (visor 3D + renders) |
| `dibujo/` | Dibujo |
| `cine/` | Cine |
| `videojuegos/` | Videojuegos (recopilación de clips + links a itch.io) |
| `ia/` | IA generativa (agentes de cada estudiante + chat) |
| `musica/` | Música |
| `fotografia/` | Fotografía |
| `programacion/` | Programación |
| `functions/api/chat.js` | Chat con los agentes de IA (Cloudflare Workers AI) |

Cada disciplina tiene:

- `index.html`: la página (diseño, textos de presentación, comportamiento).
- `data_<disciplina>.js`: la lista de estudiantes, con nombre, grupo, turno y sus trabajos. **Para cambiar datos de un estudiante, casi siempre es acá.**
- Una subcarpeta con los archivos (imágenes, videos, audios). En Dibujo y Fotografía las imágenes van empaquetadas en un `.js` por estudiante.

## IA generativa

- `ia/data_ia.js`: cada estudiante tiene un ítem `{"k": "agent", "name": ..., "desc": ..., "img": ...}` con el nombre del agente, la descripción que escribió (es la "personalidad" que usa el chat) y su imagen (`ia/ia/`).
- `functions/api/chat.js`: arma las instrucciones del personaje a partir de esa descripción y responde con un modelo de **Cloudflare Workers AI** (binding `AI`, configurado en el proyecto de Cloudflare). Ahí se puede cambiar el modelo, el largo de las respuestas o las reglas de cómo habla el agente.
- La primera pregunta a cada agente se guarda en caché un día para ahorrar cupo de IA.

## Grupos

En los datos los grupos se guardan con el primer horario (por ejemplo `Lunes 08:30`). Las páginas los muestran con los dos días ("Lun y Jue 8:30", "Mar y Jue 16:00", etc.); esa traducción está en la constante `GL` dentro de cada `index.html`.

## Contacto

Coordina: Ignacio Mendoza (Workshop Leader, TUMO Chacarita).
