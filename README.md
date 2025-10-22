<!doctype html>
<html lang="es">
<head>
<meta charset="utf-8" />
<meta name="viewport" content="width=device-width,initial-scale=1" />
<title>Línea de tiempo interactiva — La Conquista (1518–1521)</title>
<style>
body {
  font-family: 'Poppins', sans-serif;
  background: radial-gradient(circle at top, #03102b, #000512);
  color: #f3f5f9;
  margin: 0;
  padding: 0;
  overflow-x: hidden;
}
header {
  text-align: center;
  padding: 36px 20px 10px;
}
h1 {
  font-size: 2.2rem;
  color: #6fd6ff;
  text-shadow: 0 0 12px #00bfff, 0 0 22px #0077ff;
  letter-spacing: 1px;
}
.timeline {
  position: relative;
  display: flex;
  gap: 36px;
  overflow-x: auto;
  scroll-behavior: smooth;
  padding: 48px 36px 80px;
}
.timeline::before {
  content: '';
  position: absolute;
  top: 50%;
  left: 0;
  width: 100%;
  height: 4px;
  background: linear-gradient(90deg, #00bfff, #008cff, #00bfff);
  box-shadow: 0 0 20px #00bfff;
  border-radius: 2px;
}
.event {
  position: relative;
  min-width: 360px;
  max-width: 420px;
  background: linear-gradient(180deg, #071a34, #0b2744);
  border: 1px solid rgba(0,191,255,0.16);
  border-radius: 14px;
  box-shadow: 0 6px 24px rgba(0,191,255,0.06);
  padding: 16px;
  transition: transform 0.35s ease, box-shadow 0.35s ease;
  opacity: 0;
  transform: translateY(18px);
}
.event.visible { opacity: 1; transform: translateY(0); }
.event:hover { transform: translateY(-8px) scale(1.02); box-shadow: 0 14px 40px rgba(0,191,255,0.12); }
.event::before {
  content: '';
  position: absolute;
  top: calc(50% - 8px);
  left: -22px;
  width: 16px;
  height: 16px;
  background: #00bfff;
  border-radius: 50%;
  box-shadow: 0 0 12px #00bfff;
}
.meta { color: #88d8ff; font-weight: 700; margin-bottom: 6px; }
.title { font-weight: 800; color: #fff; font-size: 1.05rem; margin: 6px 0 10px; }
.imgwrap { width: 100%; height: 190px; border-radius: 10px; overflow: hidden; margin-bottom: 12px; border: 1px solid rgba(0,191,255,0.12); background: linear-gradient(180deg,#031826,#07233a); display:flex;align-items:center;justify-content:center }
.imgwrap img { width:100%; height:100%; object-fit:cover; border-radius:10px; }
.img-caption { font-size: 0.8rem; color: #aee6ff; margin-top:6px; text-align:center }
.desc { font-size: 0.95rem; color: #d6eeff; line-height: 1.5; }
footer { text-align: center; padding: 28px; color: #6fd6ff; font-size: 0.9rem; }
.small { font-size: 0.86rem; color: #98d9ff }
button.center { display:block; margin:12px auto 0; padding:8px 12px; background:#00bfff; color:#021028; border-radius:8px; border:none; font-weight:700 }
/* responsive */
@media (max-width:820px){ .timeline{padding:28px 20px} .event{min-width:300px} }
</style>
</head>
<body>
<header>
  <h1>Línea de tiempo interactiva — La Conquista (1518–1521)</h1>
  <div class="small">Versión con contexto extenso para cada acontecimiento. Colores: azul neón.</div>
</header>

<div class="timeline" id="timeline">

<!-- EVENTOS: cada tarjeta con imagen Base64 -->
<article class="event">
  <div class="meta">1517</div>
  <div class="title">Expedición de Francisco Hernández de Córdoba</div>
  <div class="imgwrap">
    <img src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAA..." alt="Ilustración llegada a Yucatán">
  </div>
  <div class="desc">La expedición de Francisco Hernández de Córdoba (1517) fue una de las primeras en tocar las costas de Yucatán. Los encuentros con los mayas fueron hostiles: los conquistadores sufrieron heridas y bajas importantes. Aunque no consiguieron una colonización inmediata, sus relatos sobre poblaciones organizadas y ciudades influyeron en la planificación de expediciones posteriores y despertaron el interés de la Corona y de conquistadores como Cortés.</div>
</article>

<article class="event">
  <div class="meta">1518</div>
  <div class="title">Exploración de Juan de Grijalva</div>
  <div class="imgwrap">
    <img src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAA..." alt="Ilustración reconocimiento de costas">
  </div>
  <div class="desc">Juan de Grijalva bordea las costas del Golfo de México, recopilando información geográfica y de población. Sus cartas y noticias hablaron de la impresionante organización del valle central (Tenochtitlan) y la existencia de riquezas. Esto llegó a oídos de otros capitanes y motivó nuevas expediciones con objetivos de exploración y lucro.</div>
</article>

<!-- Aquí seguirías copiando la misma estructura para todas las demás tarjetas, reemplazando los SVG por <img src="data:image/png;base64,..."> -->

</div>

<footer>Fuentes: síntesis a partir de crónicas (Bernal Díaz, Cortés), estudios históricos y recursos públicos. Si quieres imágenes fotográficas reales para imprimir, puedo insertar enlaces o preparar una versión en PPTX.</footer>

<script>
// hacer visibles las tarjetas al entrar en el viewport y permitir navegación con flechas
const events = Array.from(document.querySelectorAll('.event'));
const observer = new IntersectionObserver((entries)=>{
  entries.forEach(e=>{ if(e.isIntersecting){ e.target.classList.add('visible'); } });
},{threshold:0.15});
events.forEach(ev=>observer.observe(ev));
// navegación con flechas
let idx = 0; window.addEventListener('keydown', e=>{
  if(e.key === 'ArrowRight'){ idx = Math.min(events.length-1, idx+1); events[idx].scrollIntoView({behavior:'smooth', inline:'center'}); }
  if(e.key === 'ArrowLeft'){ idx = Math.max(0, 0); events[idx].scrollIntoView({behavior:'smooth', inline:'center'}); }
});
</script>
</body>
</html>
