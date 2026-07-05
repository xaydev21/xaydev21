<!DOCTYPE html>
<html>
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.1/css/all.min.css" />
  <style>
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }
    body {
      background: #0b0d15;
      color: #e0e0e0;
      font-family: 'Segoe UI', system-ui, -apple-system, sans-serif;
      padding: 2rem 1rem;
      display: flex;
      flex-direction: column;
      align-items: center;
    }
    .container {
      max-width: 1100px;
      width: 100%;
    }
    /* Header */
    .header {
      text-align: center;
      padding: 2rem 0 1rem;
    }
    .header h1 {
      font-size: 4.5rem;
      font-weight: 800;
      background: linear-gradient(135deg, #ff6b6b, #ffa94d, #f06595, #845ef7);
      -webkit-background-clip: text;
      -webkit-text-fill-color: transparent;
      background-clip: text;
      letter-spacing: 4px;
      text-shadow: 0 0 30px rgba(255, 107, 107, 0.3);
      animation: glowPulse 3s ease-in-out infinite;
    }
    @keyframes glowPulse {
      0%, 100% { text-shadow: 0 0 20px rgba(255,107,107,0.2); }
      50% { text-shadow: 0 0 40px rgba(255,107,107,0.6), 0 0 80px rgba(255,107,107,0.3); }
    }
    .subtitle {
      font-size: 1.4rem;
      font-weight: 300;
      letter-spacing: 6px;
      color: #aaa;
      margin-top: 0.5rem;
      border-right: 3px solid #ff6b6b;
      white-space: nowrap;
      overflow: hidden;
      display: inline-block;
      animation: type 4s steps(30) 1s 1 normal both, blink 0.75s step-end infinite;
      width: 0;
      max-width: 100%;
      padding-right: 6px;
    }
    @keyframes type {
      0% { width: 0; }
      100% { width: 100%; }
    }
    @keyframes blink {
      0%, 100% { border-color: transparent; }
      50% { border-color: #ff6b6b; }
    }

    /* Social Icons */
    .social-links {
      display: flex;
      justify-content: center;
      gap: 2rem;
      margin: 2rem 0;
      flex-wrap: wrap;
    }
    .social-links a {
      color: #ccc;
      font-size: 2.2rem;
      transition: all 0.3s ease;
      display: inline-block;
      text-decoration: none;
    }
    .social-links a:hover {
      color: #ff6b6b;
      transform: translateY(-6px) scale(1.1);
      text-shadow: 0 0 20px rgba(255,107,107,0.6);
    }

    /* Cards */
    .card {
      background: rgba(255,255,255,0.03);
      border: 1px solid rgba(255,255,255,0.06);
      border-radius: 20px;
      padding: 1.8rem 2rem;
      margin: 2rem 0;
      backdrop-filter: blur(6px);
      box-shadow: 0 8px 32px rgba(0,0,0,0.4);
      transition: box-shadow 0.3s;
    }
    .card:hover {
      box-shadow: 0 8px 40px rgba(255,107,107,0.15);
    }
    .card-title {
      font-size: 1.6rem;
      font-weight: 600;
      margin-bottom: 1.2rem;
      display: flex;
      align-items: center;
      gap: 0.8rem;
      color: #f0f0f0;
      border-bottom: 1px solid rgba(255,255,255,0.06);
      padding-bottom: 0.6rem;
    }
    .card-title i {
      color: #ff6b6b;
      font-size: 1.8rem;
      animation: spin 6s linear infinite;
    }
    @keyframes spin {
      0% { transform: rotate(0deg); }
      100% { transform: rotate(360deg); }
    }

    /* About Me – terminal style */
    .terminal {
      background: #0d0f17;
      padding: 1.2rem 1.6rem;
      border-radius: 12px;
      font-family: 'Fira Code', 'Consolas', monospace;
      font-size: 0.95rem;
      border-left: 4px solid #ff6b6b;
      overflow-x: auto;
      white-space: pre-wrap;
      word-break: break-word;
      line-height: 1.6;
      color: #c8d0d8;
    }
    .terminal .prompt { color: #ff6b6b; }
    .terminal .string { color: #69db7c; }
    .terminal .key { color: #ffd43b; }
    .terminal .comment { color: #868e96; }

    /* Tech Grid – Font Awesome icons */
    .tech-grid {
      display: grid;
      grid-template-columns: repeat(auto-fill, minmax(70px, 1fr));
      gap: 1.2rem;
      justify-items: center;
      margin-top: 0.5rem;
    }
    .tech-item {
      text-align: center;
      font-size: 2rem;
      color: #bbb;
      transition: all 0.3s;
      cursor: default;
    }
    .tech-item i {
      display: block;
      font-size: 2.8rem;
      margin-bottom: 0.3rem;
      transition: 0.3s;
    }
    .tech-item span {
      display: block;
      font-size: 0.65rem;
      text-transform: uppercase;
      letter-spacing: 0.5px;
      opacity: 0.6;
    }
    .tech-item:hover i {
      color: #ff6b6b;
      transform: scale(1.2) rotate(4deg);
      text-shadow: 0 0 20px rgba(255,107,107,0.4);
    }

    /* Stats */
    .stats-row {
      display: flex;
      flex-wrap: wrap;
      gap: 1rem;
      justify-content: center;
    }
    .stats-row img {
      border-radius: 12px;
      max-width: 100%;
      border: 1px solid rgba(255,255,255,0.05);
      transition: transform 0.2s;
      flex: 1 1 45%;
      min-width: 280px;
    }
    .stats-row img:hover {
      transform: scale(1.01);
    }

    /* Featured Projects – table */
    .projects-table {
      width: 100%;
      border-collapse: collapse;
      margin-top: 0.5rem;
      font-size: 0.95rem;
    }
    .projects-table th {
      text-align: left;
      color: #aaa;
      font-weight: 400;
      letter-spacing: 1px;
      padding-bottom: 0.6rem;
      border-bottom: 1px solid rgba(255,255,255,0.06);
    }
    .projects-table td {
      padding: 0.8rem 0.2rem;
      border-bottom: 1px solid rgba(255,255,255,0.04);
    }
    .projects-table tr:last-child td { border-bottom: none; }
    .projects-table .tech-tag {
      background: rgba(255,107,107,0.15);
      color: #ff6b6b;
      padding: 0.2rem 0.8rem;
      border-radius: 20px;
      font-size: 0.75rem;
      font-weight: 500;
      display: inline-block;
    }

    /* Activity bars */
    .lang-bar {
      display: flex;
      align-items: center;
      gap: 0.8rem;
      margin: 0.4rem 0;
    }
    .lang-bar .label {
      width: 100px;
      font-weight: 500;
      color: #ccc;
    }
    .lang-bar .bar-track {
      flex: 1;
      height: 6px;
      background: #2a2d3a;
      border-radius: 4px;
      overflow: hidden;
    }
    .lang-bar .bar-fill {
      height: 100%;
      border-radius: 4px;
      background: linear-gradient(90deg, #ff6b6b, #f06595);
      width: 0%;
      transition: width 1s;
    }
    .lang-bar .percent {
      width: 40px;
      text-align: right;
      font-size: 0.8rem;
      color: #aaa;
    }

    /* Focus */
    .focus-grid {
      display: flex;
      flex-wrap: wrap;
      gap: 1.2rem;
      margin-top: 0.5rem;
    }
    .focus-item {
      background: rgba(255,255,255,0.03);
      padding: 0.6rem 1.2rem;
      border-radius: 40px;
      border: 1px solid rgba(255,255,255,0.06);
      font-size: 0.9rem;
      display: flex;
      align-items: center;
      gap: 0.6rem;
    }
    .focus-item i {
      color: #ff6b6b;
      font-size: 1.2rem;
    }

    /* Footer */
    .footer {
      text-align: center;
      margin-top: 3rem;
      padding: 1.5rem 0;
      border-top: 1px solid rgba(255,255,255,0.05);
      font-size: 0.8rem;
      color: #666;
      letter-spacing: 1px;
    }
    .footer i {
      color: #ff6b6b;
      margin: 0 0.3rem;
    }
    @media (max-width: 600px) {
      .header h1 { font-size: 3rem; }
      .subtitle { font-size: 1rem; letter-spacing: 3px; }
      .social-links a { font-size: 1.8rem; }
      .tech-grid { grid-template-columns: repeat(auto-fill, minmax(60px, 1fr)); }
    }
  </style>
</head>
<body>
<div class="container">

  <!-- HEADER -->
  <div class="header">
    <h1>xaydev21</h1>
    <div class="subtitle">FULL‑STACK &bull; SECURITY &bull; AI</div>
  </div>

  <!-- SOCIAL LINKS -->
  <div class="social-links">
    <a href="https://github.com/xaydev21" title="GitHub"><i class="fab fa-github"></i></a>
    <a href="https://tiktok.com/@xaydev21" title="TikTok"><i class="fab fa-tiktok"></i></a>
    <a href="https://twitter.com/xaydev21" title="X"><i class="fab fa-x-twitter"></i></a>
  </div>

  <!-- ABOUT ME -->
  <div class="card">
    <div class="card-title"><i class="fas fa-terminal"></i> About Me</div>
    <div class="terminal">
<span class="prompt">$</span> cat about.md
<span class="comment"># xaydev21 – Full‑Stack Developer & Security Researcher</span>
<span class="key">location</span>: <span class="string">"Indonesia"</span>
<span class="key">role</span>:     <span class="string">"Full-Stack Developer · Cybersecurity Researcher"</span>
<span class="key">interests</span>: [<span class="string">"AI/ML"</span>, <span class="string">"Cloud"</span>, <span class="string">"Web Exploitation"</span>]
<span class="key">learning</span>:  <span class="string">"Rust & Advanced Penetration Testing"</span>
<span class="key">motto</span>:    <span class="string">"Secure the future, one line at a time."</span>
    </div>
  </div>

  <!-- TECH STACK -->
  <div class="card">
    <div class="card-title"><i class="fas fa-cubes"></i> Tech Arsenal</div>
    <div class="tech-grid">
      <!-- Ikon Font Awesome untuk teknologi -->
      <div class="tech-item"><i class="fab fa-python"></i><span>Python</span></div>
      <div class="tech-item"><i class="fab fa-js"></i><span>JavaScript</span></div>
      <div class="tech-item"><i class="fab fa-php"></i><span>PHP</span></div>
      <div class="tech-item"><i class="fab fa-react"></i><span>React</span></div>
      <div class="tech-item"><i class="fab fa-node-js"></i><span>Node.js</span></div>
      <div class="tech-item"><i class="fab fa-golang"></i><span>Go</span></div>
      <div class="tech-item"><i class="fas fa-cogs"></i><span>Rust</span></div>
      <div class="tech-item"><i class="fab fa-java"></i><span>Java</span></div>
      <div class="tech-item"><i class="fab fa-laravel"></i><span>Laravel</span></div>
      <div class="tech-item"><i class="fas fa-code"></i><span>Flask</span></div>
      <div class="tech-item"><i class="fas fa-code"></i><span>Django</span></div>
      <div class="tech-item"><i class="fas fa-database"></i><span>MySQL</span></div>
      <div class="tech-item"><i class="fas fa-database"></i><span>Postgres</span></div>
      <div class="tech-item"><i class="fas fa-database"></i><span>Redis</span></div>
      <div class="tech-item"><i class="fab fa-docker"></i><span>Docker</span></div>
      <div class="tech-item"><i class="fas fa-cubes"></i><span>K8s</span></div>
      <div class="tech-item"><i class="fas fa-cloud"></i><span>AWS</span></div>
      <div class="tech-item"><i class="fab fa-linux"></i><span>Linux</span></div>
      <div class="tech-item"><i class="fab fa-git-alt"></i><span>Git</span></div>
      <div class="tech-item"><i class="fab fa-github"></i><span>GitHub</span></div>
    </div>
  </div>

  <!-- STATS -->
  <div class="card">
    <div class="card-title"><i class="fas fa-chart-line"></i> GitHub Analytics</div>
    <div class="stats-row">
      <img src="https://github-readme-stats.vercel.app/api?username=xaydev21&show_icons=true&theme=radical&hide_border=true&count_private=true&bg_color=0D1117&title_color=ff6b6b&icon_color=ff6b6b&text_color=eeeeee" alt="GitHub Stats" />
      <img src="https://github-readme-streak-stats.herokuapp.com/?user=xaydev21&theme=radical&hide_border=true&background=0D1117&ring=ff6b6b&fire=ff6b6b&currStreakLabel=eeeeee" alt="GitHub Streak" />
    </div>
    <div style="display: flex; flex-wrap: wrap; gap: 1rem; justify-content: center; margin-top: 1rem;">
      <img src="https://github-readme-stats.vercel.app/api/top-langs/?username=xaydev21&layout=compact&theme=radical&hide_border=true&bg_color=0D1117&title_color=ff6b6b&text_color=eeeeee" style="flex:1 1 45%; min-width:260px; border-radius:12px;" alt="Top Languages" />
      <img src="https://github-profile-trophy.vercel.app/?username=xaydev21&theme=radical&no-frame=true&row=2&column=4&margin-w=15&margin-h=15" style="flex:1 1 45%; min-width:260px; border-radius:12px;" alt="Trophies" />
    </div>
    <div style="margin-top:1.2rem;">
      <img src="https://github-readme-activity-graph.vercel.app/graph?username=xaydev21&theme=react-dark&bg_color=0D1117&color=ff6b6b&line=ff6b6b&point=ffffff&hide_border=true" style="width:100%; border-radius:12px;" alt="Activity Graph" />
    </div>
  </div>

  <!-- FEATURED PROJECTS -->
  <div class="card">
    <div class="card-title"><i class="fas fa-rocket"></i> Featured Projects</div>
    <table class="projects-table">
      <thead><tr><th>Project</th><th>Description</th><th>Stack</th></tr></thead>
      <tbody>
        <tr><td><strong>Handschar Ransomware</strong></td><td>Advanced ransomware POC with GUI &amp; anti‑detection</td><td><span class="tech-tag">Python · AES‑256 · PyQt5</span></td></tr>
        <tr><td><strong>SouGPT</strong></td><td>Unfiltered AI assistant with custom personality</td><td><span class="tech-tag">Python · Transformers · Flask</span></td></tr>
        <tr><td><strong>X‑Auth</strong></td><td>Secure authentication microservice</td><td><span class="tech-tag">Go · JWT · PostgreSQL</span></td></tr>
        <tr><td><strong>CyberGuard</strong></td><td>Real‑time threat intelligence dashboard</td><td><span class="tech-tag">React · Node.js · WebSocket</span></td></tr>
      </tbody>
    </table>
  </div>

  <!-- ACTIVITY BARS -->
  <div class="card">
    <div class="card-title"><i class="fas fa-code-branch"></i> Weekly Activity</div>
    <div class="lang-bar"><span class="label">Python</span><div class="bar-track"><div class="bar-fill" style="width:60%;"></div></div><span class="percent">60%</span></div>
    <div class="lang-bar"><span class="label">JavaScript</span><div class="bar-track"><div class="bar-fill" style="width:30%;"></div></div><span class="percent">30%</span></div>
    <div class="lang-bar"><span class="label">Go</span><div class="bar-track"><div class="bar-fill" style="width:20%;"></div></div><span class="percent">20%</span></div>
    <div class="lang-bar"><span class="label">Rust</span><div class="bar-track"><div class="bar-fill" style="width:10%;"></div></div><span class="percent">10%</span></div>
  </div>

  <!-- CURRENT FOCUS -->
  <div class="card">
    <div class="card-title"><i class="fas fa-bullseye"></i> Current Focus</div>
    <div class="focus-grid">
      <div class="focus-item"><i class="fas fa-code"></i> Building <strong>Handschar v2.0</strong> with stealth encryption</div>
      <div class="focus-item"><i class="fas fa-book"></i> Learning <strong>Rust</strong> for system‑level security</div>
      <div class="focus-item"><i class="fas fa-handshake"></i> Collaborating on ethical hacking projects</div>
      <div class="focus-item"><i class="fas fa-envelope"></i> Reach: <strong>xaydevsupport@gmail.com</strong></div>
    </div>
  </div>

  <!-- FOOTER -->
  <div class="footer">
    <i class="fas fa-code"></i> crafted with <i class="fas fa-heart" style="color:#ff6b6b;"></i> by xaydev21 &bull; <i class="fas fa-crown"></i> 2025
  </div>

</div>
</body>
</html>
