---
name: frontend-design
description: Guía de diseño frontend/web — dirección estética con criterio, tipografía, color, layout, y reglas de responsive mobile que SÍ funcionan en celulares reales. Usar al crear o rediseñar UI, landings, componentes o pantallas, o cuando el usuario pida que algo "se vea mejor / más profesional / más lindo".
---

# Frontend Design

Guía para producir interfaces con criterio de diseño, no "AI slop". Destilado de las
buenas prácticas del agente de diseño de Claude + lecciones de responsive mobile real.

## Principio rector
**Less is more. Mil "no" por cada "sí".** Cada elemento tiene que ganarse su lugar.
Si una sección se siente vacía, es un problema de layout y composición — NO se rellena
con texto de relleno, stats inventadas, ni iconitos decorativos.

## Antes de tocar nada
1. **Entender el contexto visual existente.** Si hay marca, design system o paleta, leerlo
   y respetarlo (colores, tipografía, tono, estados hover/click, sombras, densidad, radios).
2. **Definir el sistema en voz alta** antes de codear: paleta (1–2 colores de fondo máx),
   escala tipográfica, escala de espaciado, estilo de componentes. Después, ser consistente.
3. Al sumar a una UI existente: imitar su "vocabulario visual" en vez de inventar uno nuevo.

## Evitar tropos de "AI slop"
- ❌ Gradientes de fondo agresivos.
- ❌ Emojis (salvo que la marca los use).
- ❌ Contenedores con esquinas redondeadas + borde izquierdo de color como acento.
- ❌ Dibujar imágenes/ilustraciones con SVG a mano → mejor usar placeholders y pedir el asset real.
- ❌ Fuentes sobreusadas: Inter, Roboto, Arial, Fraunces, fuentes del sistema. Elegir algo con carácter.
- ❌ "Data slop": números, stats o íconos que no aportan.

## Tipografía
- Comprometerse con una **dirección tipográfica** con personalidad.
- Escala con jerarquía clara (display / título / cuerpo / caption), no 8 tamaños random.
- `text-wrap: pretty` (cuerpo) y `text-wrap: balance` (títulos) para cortes lindos.
- Tamaños mínimos: cuerpo en web ≥ 14–16px; nunca texto crítico < 12px.

## Color
- Usar colores de la marca / design system. Si es muy restrictivo, derivar tonos armónicos
  con **oklch** a partir de la paleta existente. **No inventar colores de cero.**
- Paleta acotada. Un acento, neutros, y poco más. El color se gana su lugar.

## Layout y espaciado
- **CSS Grid** y flexbox son tus amigos; usar layouts no obvios cuando aporten.
- Ritmo visual con escala de espaciado consistente (ej. múltiplos de 4px).
- El whitespace es diseño, no espacio desperdiciado. Jerarquía por tamaño/peso/espacio, no por cajas.

## Dar opciones
Cuando se exploran diseños, ofrecer 3+ variaciones en distintas dimensiones (visual,
interacción, color), de lo más by-the-book a lo más creativo. Mezclar y combinar.

## Responsive mobile — reglas que SÍ funcionan en celulares reales
> El modo responsive del F12 **no** simula la barra del navegador, las safe-areas ni el
> tamaño de fuente del sistema. **Siempre validar en celular real** (o tenerlo en cuenta).

- **Alturas:** usar `100dvh` (dynamic viewport) en vez de `100vh`. `100vh` en mobile es el
  viewport con la barra OCULTA → más alto que el área visible → contenido cortado abajo.
- **OJO con bloquear scroll** (`overflow:hidden` en body): si el contenido no entra, el botón
  de abajo queda inalcanzable y la barra del navegador NO se colapsa (solo colapsa al scrollear).
  Si dudás, **permitir scroll**.
- **Safe areas:** padding con `env(safe-area-inset-bottom/top)` para notch y barra de gestos.
- **Hit targets ≥ 44px** de alto/área tocable. Botones y links cómodos para el dedo.
- **Patrón robusto "todo en pantalla":** header fijo arriba + footer/botones fijos abajo
  (`position: sticky`/`fixed` con safe-area), y dejar que SOLO la zona de contenido del medio
  scrollee si no entra. Así los botones nunca se escapan, aunque la barra del navegador tape espacio.
- Tamaños atados al alto (`vh`/`dvh` con `clamp()`) solo si de verdad necesitás que entre sin scroll;
  recordá que ahí el texto se achica en pantallas bajas.

## Contenido
- **No agregar material sin preguntar.** Si creés que sumar secciones/copy mejora el diseño,
  consultá primero. El usuario conoce su audiencia mejor.
- Imágenes faltantes → placeholder claro, mejor que un intento malo del asset real.

## Verificar
- Probar en varios tamaños (incluyendo un celular bajo, ~360×540) y, si es posible, en device real.
- Chequear que no haya texto cortado, botones inalcanzables, ni scroll inesperado.
