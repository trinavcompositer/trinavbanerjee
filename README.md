<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<meta name="description" content="Trinav Banerjee — Compositing Supervisor and senior VFX professional portfolio.">
<title>Trinav Banerjee | Compositing Supervisor</title>

<style>
@import url('https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700;800&family=Space+Grotesk:wght@400;500;600;700&display=swap');

:root{
  --bg:#05070b; --panel:rgba(15,19,28,.72); --line:rgba(255,255,255,.10);
  --text:#f4f7fb; --muted:#9aa5b5; --accent:#65d9ff; --accent2:#9b7cff;
}
*{box-sizing:border-box;margin:0;padding:0}
html{scroll-behavior:smooth}
body{
  background:var(--bg); color:var(--text); font-family:Inter,Arial,sans-serif;
  overflow-x:hidden; line-height:1.6;
}
a{color:inherit;text-decoration:none}
#canvas{position:fixed;inset:0;width:100%;height:100%;z-index:-3}
.grid-bg{
  position:fixed;inset:0;z-index:-2;pointer-events:none;opacity:.22;
  background-image:linear-gradient(rgba(255,255,255,.04) 1px,transparent 1px),
                   linear-gradient(90deg,rgba(255,255,255,.04) 1px,transparent 1px);
  background-size:55px 55px;
  mask-image:linear-gradient(to bottom,black,transparent 80%);
}
.glow{position:fixed;border-radius:50%;filter:blur(90px);z-index:-2;pointer-events:none}
.glow.one{width:360px;height:360px;background:rgba(101,217,255,.13);top:5%;left:-100px}
.glow.two{width:420px;height:420px;background:rgba(155,124,255,.12);right:-150px;top:30%}
.container{width:min(1160px,92%);margin:auto}
nav{
  position:fixed;top:0;left:0;right:0;z-index:20;
  backdrop-filter:blur(18px);background:rgba(5,7,11,.65);border-bottom:1px solid var(--line)
}
.nav-inner{height:74px;display:flex;align-items:center;justify-content:space-between}
.logo{font-family:"Space Grotesk";font-weight:700;letter-spacing:.5px}
.logo span{color:var(--accent)}
.navlinks{display:flex;gap:28px;font-size:14px;color:var(--muted)}
.navlinks a:hover{color:white}
.hero{min-height:100vh;display:grid;place-items:center;padding:130px 0 70px}
.hero-content{text-align:center;max-width:920px}
.badge{
  display:inline-flex;align-items:center;gap:8px;padding:8px 14px;border:1px solid var(--line);
  border-radius:100px;background:rgba(255,255,255,.035);color:#c7d0dd;font-size:12px;
  text-transform:uppercase;letter-spacing:2px
}
.dot{width:7px;height:7px;border-radius:50%;background:#6effb1;box-shadow:0 0 16px #6effb1}
h1{
  font-family:"Space Grotesk";font-size:clamp(48px,9vw,104px);line-height:.95;
  margin:26px 0 18px;letter-spacing:-4px
}
.gradient{background:linear-gradient(100deg,#fff 15%,var(--accent),#b79cff 75%);-webkit-background-clip:text;background-clip:text;color:transparent}
.hero p{font-size:clamp(16px,2vw,20px);color:var(--muted);max-width:720px;margin:0 auto 32px}
.buttons{display:flex;justify-content:center;gap:14px;flex-wrap:wrap}
.btn{
  display:inline-flex;align-items:center;justify-content:center;gap:9px;padding:13px 22px;
  border-radius:10px;border:1px solid var(--line);font-weight:600;font-size:14px;transition:.25s;
}
.btn.primary{background:white;color:#080a0e;border-color:white}
.btn:hover{transform:translateY(-3px);box-shadow:0 12px 35px rgba(0,0,0,.35)}
.btn.secondary{background:rgba(255,255,255,.04)}
section{padding:100px 0}
.section-head{margin-bottom:34px}
.kicker{color:var(--accent);font-size:12px;text-transform:uppercase;letter-spacing:3px;font-weight:700}
h2{font-family:"Space Grotesk";font-size:clamp(30px,5vw,48px);margin-top:8px}
.sub{color:var(--muted);max-width:680px;margin-top:10px}
.cards{display:grid;grid-template-columns:repeat(2,1fr);gap:18px}
.card{
  background:var(--panel);border:1px solid var(--line);border-radius:18px;padding:28px;
  backdrop-filter:blur(15px);transition:.3s;position:relative;overflow:hidden
}
.card:before{
  content:"";position:absolute;inset:-1px;opacity:0;transition:.3s;
  background:radial-gradient(circle at var(--x,50%) var(--y,50%),rgba(101,217,255,.14),transparent 35%)
}
.card:hover{transform:translateY(-5px);border-color:rgba(101,217,255,.3)}
.card:hover:before{opacity:1}
.card>*{position:relative}
.card-icon{font-size:28px;margin-bottom:16px}
.card h3{font-family:"Space Grotesk";font-size:22px;margin-bottom:6px}
.card p{color:var(--muted);font-size:14px}
.arrow{float:right;color:var(--accent);font-size:20px}
.stats{display:grid;grid-template-columns:repeat(3,1fr);gap:18px;margin-top:18px}
.stat{padding:25px;border:1px solid var(--line);border-radius:16px;background:rgba(255,255,255,.025);text-align:center}
.stat strong{display:block;font-family:"Space Grotesk";font-size:34px}
.stat span{font-size:12px;color:var(--muted);text-transform:uppercase;letter-spacing:1.5px}
.contact-box{
  text-align:center;padding:65px 25px;border-radius:24px;border:1px solid var(--line);
  background:linear-gradient(135deg,rgba(101,217,255,.08),rgba(155,124,255,.08));
}
.contact-box p{color:var(--muted);max-width:600px;margin:12px auto 28px}
.contact-links{display:flex;justify-content:center;gap:12px;flex-wrap:wrap}
footer{border-top:1px solid var(--line);padding:28px 0;color:#687384;font-size:12px}
footer .container{display:flex;justify-content:space-between;gap:20px;flex-wrap:wrap}
@media(max-width:700px){
  .navlinks{display:none}.cards,.stats{grid-template-columns:1fr}
  h1{letter-spacing:-2px}.hero{padding-top:110px}section{padding:75px 0}
}

.resume-wrap{max-width:1000px;margin:auto}
.resume-sheet{background:rgba(255,255,255,.97);color:#17202b;border-radius:20px;padding:42px;box-shadow:0 25px 70px rgba(0,0,0,.38);position:relative;overflow:hidden}
.resume-sheet:before{content:"";position:absolute;top:0;left:0;right:0;height:5px;background:linear-gradient(90deg,var(--accent),var(--accent2))}
.resume-top{display:flex;justify-content:space-between;gap:30px;border-bottom:1px solid #dce1e8;padding-bottom:24px}
.resume-name{font-family:"Space Grotesk";font-size:38px;font-weight:700;letter-spacing:-1px}
.resume-role{font-size:18px;color:#536174;margin-top:4px}
.resume-contact{text-align:right;font-size:13px;color:#536174;line-height:1.9}
.resume-contact a{color:#536174}
.resume-section{margin-top:28px}
.resume-section h3{font-family:"Space Grotesk";font-size:14px;text-transform:uppercase;letter-spacing:2px;color:#344256;border-bottom:1px solid #dce1e8;padding-bottom:8px;margin-bottom:12px}
.resume-summary{font-size:14px;line-height:1.8;color:#465365}
.resume-job{margin-bottom:20px}
.resume-job-head{display:flex;justify-content:space-between;gap:20px}
.resume-job h4{font-size:16px}.resume-job .role{color:#59677a;font-size:14px}.resume-job .date{font-size:13px;color:#69778a;white-space:nowrap}
.resume-job ul{margin:8px 0 0 18px;color:#465365;font-size:13px}.resume-job li{margin:4px 0}
.resume-grid{display:grid;grid-template-columns:1fr 1fr;gap:25px}
.resume-list{color:#465365;font-size:13px;line-height:1.9}.resume-list strong{color:#273548}
.resume-list a{text-decoration:underline}
@media(max-width:700px){.resume-sheet{padding:25px 20px}.resume-top{display:block}.resume-contact{text-align:left;margin-top:12px}.resume-name{font-size:30px}.resume-job-head{display:block}.resume-job .date{display:block;margin-top:3px}.resume-grid{grid-template-columns:1fr}}


.video-background{
  position:fixed; inset:0; z-index:-5; overflow:hidden; pointer-events:none;
  background:#03050a;
}
.video-background iframe{
  position:absolute; top:50%; left:50%; width:177.78vh; height:100vh;
  min-width:100vw; min-height:56.25vw; transform:translate(-50%,-50%);
  border:0; opacity:.62; filter:saturate(1.35) contrast(1.08);
}
.video-overlay{
  position:fixed; inset:0; z-index:-4; pointer-events:none;
  background:
    linear-gradient(180deg,rgba(2,5,12,.55) 0%,rgba(4,6,14,.72) 48%,rgba(3,5,10,.94) 100%),
    radial-gradient(circle at 12% 20%,rgba(0,225,255,.18),transparent 28%),
    radial-gradient(circle at 88% 25%,rgba(171,79,255,.20),transparent 30%),
    radial-gradient(circle at 50% 75%,rgba(255,71,146,.12),transparent 30%);
}
.glow.one{background:rgba(0,224,255,.22);animation:floatGlow 9s ease-in-out infinite}
.glow.two{background:rgba(172,87,255,.20);animation:floatGlow 12s ease-in-out infinite reverse}
@keyframes floatGlow{
  0%,100%{transform:translate3d(0,0,0) scale(1)}
  50%{transform:translate3d(35px,-25px,0) scale(1.12)}
}
.profile{
  background:linear-gradient(135deg,rgba(14,24,38,.82),rgba(30,15,48,.72));
  border-color:rgba(102,220,255,.22);
}
.badge{border-color:rgba(101,217,255,.28);box-shadow:0 0 25px rgba(101,217,255,.08)}
.btn.primary{
  background:linear-gradient(100deg,#fff,#bcefff);border-color:transparent;
}
.card{
  background:linear-gradient(135deg,rgba(15,23,38,.76),rgba(26,16,43,.70));
}

</style>
</head>

<body>

<!-- Cinematic Vimeo Background -->
<div class="video-background" aria-hidden="true">
  <iframe
    src="https://player.vimeo.com/video/743427392?background=1&autoplay=1&muted=1&loop=1&autopause=0&title=0&byline=0&portrait=0"
    frameborder="0"
    allow="autoplay; fullscreen; picture-in-picture"
    title="Vimeo background">
  </iframe>
</div>
<div class="video-overlay"></div>

<canvas id="canvas"></canvas>
<div class="grid-bg"></div>
<div class="glow one"></div><div class="glow two"></div>

<nav>
  <div class="container nav-inner">
    <a class="logo" href="#">TRINAV<span>.</span></a>
    <div class="navlinks">
      <a href="#work">Work</a><a href="#profiles">Profiles</a><a href="#about">About</a><a href="#resume">Resume</a><a href="#contact">Contact</a>
    </div>
  </div>
</nav>

<main>
<section class="hero">
  <div class="container hero-content">
    <div class="badge"><span class="dot"></span> Available for opportunities</div>
    <h1>Trinav <span class="gradient">Banerjee</span></h1>
    <p>Compositing Supervisor · VFX Artist · Creative Problem Solver<br>
       Bringing cinematic imagery, technical precision and team leadership together.</p>
    <div class="buttons">
      <a class="btn primary" href="#contact">✦ Hire Me</a>
      <a class="btn secondary" href="mailto:trinav.banerjee@gmail.com">✉ Contact Me</a>
      <a class="btn secondary" href="#work">View Portfolio ↓</a>
      <a class="btn secondary" href="#resume">📄 View Resume</a>
    </div>
  </div>
</section>

<section id="work">
  <div class="container">
    <div class="section-head">
      <div class="kicker">Selected Work</div>
      <h2>Portfolio & Showreel</h2>
      <p class="sub">Explore selected work, reels and professional profiles.</p>
    </div>
    <div class="cards">
      <a class="card" href="https://vimeo.com/743427392" target="_blank" rel="noopener noreferrer">
        <span class="arrow">↗</span><div class="card-icon">◉</div>
        <h3>Vimeo Portfolio</h3><p>Selected VFX and compositing work.</p>
      </a>
      <a class="card" href="https://youtu.be/QHU8y1oKWDE?si=JZy_mNZgASNvdtio" target="_blank" rel="noopener noreferrer">
        <span class="arrow">↗</span><div class="card-icon">▶</div>
        <h3>YouTube Showreel</h3><p>Watch my reel and video work.</p>
      </a>
    </div>
    <div class="stats">
      <div class="stat"><strong>16+</strong><span>Years Experience</span></div>
      <div class="stat"><strong>12+</strong><span>Years Supervisory Experience</span></div>
      <div class="stat"><strong>VFX</strong><span>Compositing & Supervision</span></div>
    </div>
  </div>
</section>

<section id="profiles">
  <div class="container">
    <div class="section-head">
      <div class="kicker">Professional Presence</div>
      <h2>Find Me Online</h2>
      <p class="sub">Connect, collaborate or explore my professional credits.</p>
    </div>
    <div class="cards">
      <a class="card" href="Trinav_Banerjee_Resume.pdf" target="_blank" rel="noopener noreferrer">
        <span class="arrow">↗</span><div class="card-icon">▣</div>
        <h3>My Resume</h3><p>Open my complete professional resume in PDF format.</p>
      </a>
      <a class="card" href="https://www.linkedin.com/in/trinav-banerjee-36547547" target="_blank" rel="noopener noreferrer">
        <span class="arrow">↗</span><div class="card-icon">in</div>
        <h3>LinkedIn</h3><p>Professional profile, experience and networking.</p>
      </a>
      <a class="card" href="https://www.imdb.com/name/nm8002301/?ref_=ext_shr" target="_blank" rel="noopener noreferrer">
        <span class="arrow">↗</span><div class="card-icon">★</div>
        <h3>IMDb</h3><p>Industry credits and professional filmography.</p>
      </a>
    </div>
  </div>
</section>

<section id="about">
  <div class="container">
    <div class="section-head">
      <div class="kicker">Profile</div>
      <h2>Crafting the Invisible.</h2>
      <p class="sub">
        Senior compositing professional focused on delivering polished, cinematic shots while
        balancing artistic quality, technical workflows, deadlines and team collaboration.
      </p>
    </div>
  </div>
</section>


<section id="resume">
  <div class="container">
    <div class="section-head">
      <div class="kicker">Curriculum Vitae</div>
      <h2>Professional Resume</h2>
      <p class="sub">My professional experience, skills and education are presented directly on this page.</p>
    </div>
    <div class="resume-wrap">
      <article class="resume-sheet">
        <div class="resume-top">
          <div>
            <div class="resume-name">TRINAV BANERJEE</div>
            <div class="resume-role">COMPOSITING SUPERVISOR</div>
          </div>
          <div class="resume-contact">
            Konnagar<br>
            <a href="mailto:trinav.banerjee@gmail.com">trinav.banerjee@gmail.com</a>
          </div>
        </div>
        <div class="resume-section">
          <h3>Profile</h3>
          <p class="resume-summary">Experienced Compositing Supervisor and Senior Compositor with 16+ years of professional experience in the visual effects and animation industry, including 12+ years in compositing supervision and team leadership. Strong background in leading compositing teams, managing complex shots and sequences, maintaining visual consistency, troubleshooting technical and creative challenges, and delivering high-quality work within demanding production schedules.</p>
        </div>
        <div class="resume-section">
          <h3>Career Highlights</h3>
          <div class="resume-grid">
            <div class="resume-list"><div>• <strong>16+ years</strong> of professional VFX and compositing experience</div><div>• <strong>12+ years</strong> of compositing supervision experience</div></div>
            <div class="resume-list"><div>• Strong focus on quality, efficiency and production delivery</div><div>• Extensive experience in Nuke-based compositing</div></div>
          </div>
        </div>
        <div class="resume-section">
          <h3>Work Experience</h3>
          <div class="resume-job"><div class="resume-job-head"><div><h4>Cloud House Animation Studio Pvt. Ltd.</h4><div class="role">Compositing Supervisor</div></div><div class="date">2023 – Present</div></div><ul><li>Freej 6, Puffins Impossible, PRAN Drinko TVC, Drone Cats Series, Little Singham, Young Achiever, Teela Tola and other international and domestic series.</li></ul></div>
          <div class="resume-job"><div class="resume-job-head"><div><h4>BFX CGI Animation Studios Pvt. Ltd.</h4><div class="role">Compositing Supervisor</div></div><div class="date">2016 – 2023</div></div><ul><li>Knight Rusty; Chhota Bheem Kung Fu Dhamaka; Belka &amp; Strelka 3; Lego Hidden; LCSV; Lego Boo; Build Animals; Klick; Dumpling Toy Music Videos; and many more commercials.</li></ul></div>
          <div class="resume-job"><div class="resume-job-head"><div><h4>Tripwire Vision Works</h4><div class="role">Sr. Compositer</div></div><div class="date">2011 – 2016</div></div><ul><li>Belka &amp; Strelka; Belka &amp; Strelka 2; many other commercials and game teasers.</li></ul></div>
          <div class="resume-job"><div class="resume-job-head"><div><h4>Prime Focus Ltd.</h4><div class="role">VFX Paint Artist</div></div><div class="date">2010 – 2011</div></div><ul><li>Clash of the Titans; Harry Potter HBD; Harry Potter DH; Star Wars; Season of the Witch; Shrek the Third; Cats &amp; Dogs and many movies.</li></ul></div>
          <div class="resume-job"><div class="resume-job-head"><div><h4>UNO Digital</h4><div class="role">Roto and Paint Artist</div></div><div class="date">2009 – 2010</div></div><ul><li>Alice in Wonderland (A Walt Disney production); Transformer 2 (Promo) and other work.</li></ul></div>
        </div>
        <div class="resume-section">
          <h3>Skills &amp; Core Expertise</h3>
          <div class="resume-grid">
            <div class="resume-list"><div><strong>Software:</strong> Nuke, Fusion, Blender, After Effects, Premier</div><div><strong>Language:</strong> English, Hindi, Bengali</div></div>
            <div class="resume-list"><div><strong>Core Expertise:</strong> CG Integration, Matte Painting Integration, Colour &amp; Image Integration</div><div><strong>Production:</strong> Plate Preparation &amp; Cleanup, Time Management, Good Team Player, Hard Work, Fast Learner, Deadline &amp; Delivery Management</div></div>
          </div>
        </div>
        <div class="resume-section">
          <h3>Education</h3>
          <p class="resume-summary">MAAC — Advanced Diploma in 3D Animation and VFX (2007–2009). Worked on 24 FPS as a main compositor in 2009.</p>
        </div>
        
      </article>
      
    </div>
  </div>
</section>

<section id="contact">
  <div class="container">
    <div class="contact-box">
      <div class="kicker">Let's Work Together</div>
      <h2>Have a project in mind?</h2>
      <p>I'm open to professional opportunities, VFX projects, compositing supervision and creative collaborations.</p>
      <div class="contact-links">
        <a class="btn primary" href="mailto:trinav.banerjee@gmail.com">✉ trinav.banerjee@gmail.com</a>
        <a class="btn secondary" href="tel:+919007361663">☎ 9007361663</a>
        <a class="btn secondary" href="tel:+918100170310">☎ 8100170310</a>
      </div>
    </div>
  </div>
</section>
</main>

<footer>
  <div class="container">
    <span>© 2026 Trinav Banerjee</span>
    <span>Compositing Supervisor · VFX Professional</span>
  </div>
</footer>

<script>
// Lightweight animated particle/circuit background
const canvas=document.getElementById("canvas"),ctx=canvas.getContext("2d");
let w,h,pts=[];
function resize(){
  w=canvas.width=innerWidth*devicePixelRatio;
  h=canvas.height=innerHeight*devicePixelRatio;
  canvas.style.width=innerWidth+"px"; canvas.style.height=innerHeight+"px";
  ctx.setTransform(devicePixelRatio,0,0,devicePixelRatio,0,0);
  pts=Array.from({length:Math.min(75,Math.floor(innerWidth/16))},()=>({
    x:Math.random()*innerWidth,y:Math.random()*innerHeight,
    vx:(Math.random()-.5)*.25,vy:(Math.random()-.5)*.25,r:Math.random()*1.5+.4
  }));
}
function draw(){
  ctx.clearRect(0,0,innerWidth,innerHeight);
  for(const p of pts){p.x+=p.vx;p.y+=p.vy;
    if(p.x<0||p.x>innerWidth)p.vx*=-1;if(p.y<0||p.y>innerHeight)p.vy*=-1;
    ctx.beginPath();ctx.arc(p.x,p.y,p.r,0,Math.PI*2);ctx.fillStyle="rgba(160,210,255,.5)";ctx.fill();
  }
  for(let i=0;i<pts.length;i++)for(let j=i+1;j<pts.length;j++){
    const a=pts[i],b=pts[j],dx=a.x-b.x,dy=a.y-b.y,d=Math.hypot(dx,dy);
    if(d<120){ctx.beginPath();ctx.moveTo(a.x,a.y);ctx.lineTo(b.x,b.y);
      ctx.strokeStyle=`rgba(130,170,220,${(1-d/120)*.12})`;ctx.stroke();}
  }
  requestAnimationFrame(draw);
}
addEventListener("resize",resize);resize();draw();

document.querySelectorAll(".card").forEach(card=>{
  card.addEventListener("mousemove",e=>{
    const r=card.getBoundingClientRect();
    card.style.setProperty("--x",((e.clientX-r.left)/r.width*100)+"%");
    card.style.setProperty("--y",((e.clientY-r.top)/r.height*100)+"%");
  });
});
</script>
</body>
</html>
