<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Tanmay Kundu — Android & Mobile Developer</title>
<link href="https://fonts.googleapis.com/css2?family=Space+Mono:wght@400;700&family=Syne:wght@400;500;600;700;800&family=DM+Sans:ital,wght@0,300;0,400;0,500;1,300&display=swap" rel="stylesheet">
<style>
  :root {
    --c1: #00E5FF;
    --c2: #00FF94;
    --c3: #FF6B6B;
    --c4: #FFD93D;
    --c5: #A855F7;
    --c6: #FF8C42;
    --dark: #080C14;
    --dark2: #0D1421;
    --dark3: #111827;
    --glass: rgba(255,255,255,0.04);
    --glass2: rgba(255,255,255,0.08);
    --border: rgba(255,255,255,0.08);
  }
  * { margin: 0; padding: 0; box-sizing: border-box; }
  html { scroll-behavior: smooth; }
  body { background: var(--dark); color: #E2E8F0; font-family: 'DM Sans', sans-serif; overflow-x: hidden; cursor: none; }

  .cursor { position: fixed; width: 12px; height: 12px; background: var(--c1); border-radius: 50%; pointer-events: none; z-index: 9999; mix-blend-mode: difference; transition: transform 0.1s ease; }
  .cursor-ring { position: fixed; width: 36px; height: 36px; border: 1.5px solid var(--c1); border-radius: 50%; pointer-events: none; z-index: 9998; transition: all 0.15s ease; opacity: 0.6; }

  .grid-bg { position: fixed; inset: 0; z-index: 0; background-image: linear-gradient(rgba(0,229,255,0.03) 1px, transparent 1px), linear-gradient(90deg, rgba(0,229,255,0.03) 1px, transparent 1px); background-size: 60px 60px; animation: gridMove 20s linear infinite; }
  @keyframes gridMove { 0%{background-position:0 0;} 100%{background-position:60px 60px;} }

  .blob { position: fixed; border-radius: 50%; filter: blur(120px); pointer-events: none; z-index: 0; opacity: 0.12; animation: blobFloat 8s ease-in-out infinite; }
  .blob1 { width: 500px; height: 500px; background: var(--c1); top: -100px; right: -100px; animation-delay: 0s; }
  .blob2 { width: 400px; height: 400px; background: var(--c5); bottom: 10%; left: -100px; animation-delay: -3s; }
  .blob3 { width: 300px; height: 300px; background: var(--c2); top: 50%; left: 50%; animation-delay: -5s; }
  @keyframes blobFloat { 0%,100%{transform:translate(0,0) scale(1);} 50%{transform:translate(30px,-30px) scale(1.1);} }

  nav { position: fixed; top: 0; left: 0; right: 0; z-index: 100; padding: 20px 60px; display: flex; align-items: center; justify-content: space-between; background: rgba(8,12,20,0.85); backdrop-filter: blur(20px); border-bottom: 1px solid var(--border); }
  .nav-logo { font-family: 'Space Mono', monospace; font-size: 1rem; color: var(--c1); letter-spacing: 2px; }
  .nav-links { display: flex; gap: 36px; }
  .nav-links a { color: rgba(255,255,255,0.5); text-decoration: none; font-size: 0.82rem; letter-spacing: 1.5px; text-transform: uppercase; transition: color 0.3s; font-family: 'Space Mono', monospace; }
  .nav-links a:hover { color: var(--c1); }

  section { position: relative; z-index: 1; }

  .hero { min-height: 100vh; display: flex; flex-direction: column; justify-content: center; padding: 120px 60px 80px; position: relative; overflow: hidden; }

  .hero-tag { display: inline-flex; align-items: center; gap: 8px; background: rgba(0,229,255,0.1); border: 1px solid rgba(0,229,255,0.25); color: var(--c1); padding: 6px 16px; border-radius: 100px; font-family: 'Space Mono', monospace; font-size: 0.72rem; letter-spacing: 2px; text-transform: uppercase; margin-bottom: 30px; width: fit-content; animation: fadeUp 0.8s ease both; }
  .tag-dot { width: 6px; height: 6px; border-radius: 50%; background: var(--c2); animation: pulse 1.5s infinite; }
  @keyframes pulse { 0%,100%{opacity:1;transform:scale(1);} 50%{opacity:0.5;transform:scale(1.5);} }

  .hero h1 { font-family: 'Syne', sans-serif; font-size: clamp(52px, 8vw, 110px); font-weight: 800; line-height: 0.95; margin-bottom: 24px; animation: fadeUp 0.8s 0.1s ease both; }
  .hero h1 .line1 { display: block; color: #fff; }
  .hero h1 .line2 { display: block; background: linear-gradient(90deg, var(--c1), var(--c2), var(--c5)); -webkit-background-clip: text; -webkit-text-fill-color: transparent; background-clip: text; animation: gradientShift 4s ease infinite; background-size: 200%; }
  @keyframes gradientShift { 0%,100%{background-position:0%;} 50%{background-position:100%;} }

  .hero-desc { font-size: 1.1rem; color: rgba(255,255,255,0.5); max-width: 580px; line-height: 1.8; margin-bottom: 40px; animation: fadeUp 0.8s 0.2s ease both; }

  .hero-actions { display: flex; gap: 16px; flex-wrap: wrap; animation: fadeUp 0.8s 0.3s ease both; }
  .btn-primary { background: var(--c1); color: var(--dark); padding: 14px 32px; border-radius: 100px; font-weight: 700; font-size: 0.9rem; text-decoration: none; letter-spacing: 0.5px; transition: all 0.3s; border: none; cursor: pointer; font-family: 'Space Mono', monospace; }
  .btn-primary:hover { transform: translateY(-3px); box-shadow: 0 20px 40px rgba(0,229,255,0.3); }
  .btn-outline { background: transparent; color: #fff; padding: 14px 32px; border-radius: 100px; font-weight: 500; font-size: 0.9rem; text-decoration: none; border: 1px solid var(--border); transition: all 0.3s; cursor: pointer; font-family: 'Space Mono', monospace; }
  .btn-outline:hover { border-color: rgba(255,255,255,0.4); transform: translateY(-3px); }

  .hero-stats { display: flex; gap: 20px; margin-top: 60px; flex-wrap: wrap; animation: fadeUp 0.8s 0.4s ease both; }
  .stat-card { background: var(--glass2); border: 1px solid var(--border); border-radius: 16px; padding: 20px 28px; backdrop-filter: blur(10px); transition: all 0.3s; }
  .stat-card:hover { border-color: var(--c1); transform: translateY(-4px); }
  .stat-val { font-family: 'Syne', sans-serif; font-size: 2.2rem; font-weight: 800; background: linear-gradient(135deg, var(--c1), var(--c2)); -webkit-background-clip: text; -webkit-text-fill-color: transparent; background-clip: text; }
  .stat-label { font-size: 0.75rem; color: rgba(255,255,255,0.4); letter-spacing: 1px; text-transform: uppercase; margin-top: 4px; }

  .views-banner { position: absolute; top: 130px; right: 60px; background: var(--glass2); border: 1px solid rgba(0,255,148,0.3); border-radius: 16px; padding: 16px 24px; backdrop-filter: blur(20px); animation: fadeUp 0.8s 0.5s ease both; }
  .views-row { display: flex; align-items: center; gap: 10px; }
  .views-count { font-family: 'Syne', sans-serif; font-size: 1.6rem; font-weight: 800; color: var(--c2); }
  .views-label { font-size: 0.7rem; color: rgba(255,255,255,0.4); letter-spacing: 1px; text-transform: uppercase; margin-top: 2px; }
  .views-live { display: flex; align-items: center; gap: 6px; font-size: 0.68rem; color: var(--c2); margin-top: 8px; }
  .live-dot { width: 5px; height: 5px; border-radius: 50%; background: var(--c2); animation: pulse 1s infinite; }

  .phone-frame-float { position: absolute; right: 80px; bottom: 40px; width: 160px; height: 320px; border: 2.5px solid rgba(0,229,255,0.25); border-radius: 36px; background: linear-gradient(135deg, rgba(0,229,255,0.05), rgba(168,85,247,0.05)); display: flex; flex-direction: column; align-items: center; justify-content: center; gap: 12px; animation: phoneFloat 6s ease-in-out infinite; box-shadow: 0 0 60px rgba(0,229,255,0.08), inset 0 0 40px rgba(0,229,255,0.03); opacity: 0.6; }
  .phone-frame-float .ph-notch { width: 50px; height: 8px; background: rgba(255,255,255,0.15); border-radius: 100px; position: absolute; top: 16px; }
  .phone-frame-float .ph-icon { font-size: 2.5rem; }
  .phone-frame-float .ph-label { font-family: 'Space Mono', monospace; font-size: 0.45rem; color: rgba(255,255,255,0.3); text-align: center; letter-spacing: 2px; }
  .ph-bar { width: 40px; height: 3px; border-radius: 100px; position: absolute; bottom: 16px; }
  @keyframes phoneFloat { 0%,100%{transform:translateY(0) rotate(3deg);} 50%{transform:translateY(-16px) rotate(3deg);} }

  @keyframes fadeUp { from{opacity:0;transform:translateY(40px);} to{opacity:1;transform:translateY(0);} }

  .reveal { opacity: 0; transform: translateY(50px); transition: all 0.8s cubic-bezier(0.16,1,0.3,1); }
  .reveal.visible { opacity: 1; transform: translateY(0); }
  .reveal-left { opacity: 0; transform: translateX(-50px); transition: all 0.8s cubic-bezier(0.16,1,0.3,1); }
  .reveal-left.visible { opacity: 1; transform: translateX(0); }
  .reveal-right { opacity: 0; transform: translateX(50px); transition: all 0.8s cubic-bezier(0.16,1,0.3,1); }
  .reveal-right.visible { opacity: 1; transform: translateX(0); }

  .section-wrap { padding: 100px 60px; max-width: 1300px; margin: 0 auto; }

  .sec-eyebrow { font-family: 'Space Mono', monospace; font-size: 0.72rem; color: var(--c1); letter-spacing: 3px; text-transform: uppercase; margin-bottom: 12px; display: flex; align-items: center; gap: 12px; }
  .sec-eyebrow::after { content: ''; flex: 1; max-width: 60px; height: 1px; background: var(--c1); opacity: 0.4; }
  .sec-title { font-family: 'Syne', sans-serif; font-size: clamp(32px, 4vw, 52px); font-weight: 800; color: #fff; line-height: 1.1; }
  .sec-title span { background: linear-gradient(90deg, var(--c4), var(--c6)); -webkit-background-clip: text; -webkit-text-fill-color: transparent; background-clip: text; }

  .sec-header { margin-bottom: 60px; }

  .about-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 60px; align-items: center; }
  .about-text p { color: rgba(255,255,255,0.6); line-height: 1.9; font-size: 1rem; margin-bottom: 20px; }
  .about-tags { display: flex; flex-wrap: wrap; gap: 10px; margin-top: 30px; }
  .tag { padding: 6px 16px; border-radius: 100px; font-size: 0.78rem; font-weight: 500; border: 1px solid; letter-spacing: 0.5px; }
  .tag-cyan { color: var(--c1); border-color: rgba(0,229,255,0.3); background: rgba(0,229,255,0.06); }
  .tag-green { color: var(--c2); border-color: rgba(0,255,148,0.3); background: rgba(0,255,148,0.06); }
  .tag-purple { color: var(--c5); border-color: rgba(168,85,247,0.3); background: rgba(168,85,247,0.06); }
  .tag-yellow { color: var(--c4); border-color: rgba(255,217,61,0.3); background: rgba(255,217,61,0.06); }
  .tag-red { color: var(--c3); border-color: rgba(255,107,107,0.3); background: rgba(255,107,107,0.06); }
  .tag-orange { color: var(--c6); border-color: rgba(255,140,66,0.3); background: rgba(255,140,66,0.06); }

  .about-visual { display: flex; flex-direction: column; gap: 14px; }
  .info-card { background: var(--glass); border: 1px solid var(--border); border-radius: 16px; padding: 18px 22px; display: flex; align-items: center; gap: 16px; transition: all 0.3s; }
  .info-card:hover { border-color: rgba(255,255,255,0.15); transform: translateX(8px); }
  .info-icon { width: 42px; height: 42px; border-radius: 12px; display: flex; align-items: center; justify-content: center; font-size: 1.2rem; flex-shrink: 0; }
  .info-icon.cyan { background: rgba(0,229,255,0.1); }
  .info-icon.green { background: rgba(0,255,148,0.1); }
  .info-icon.purple { background: rgba(168,85,247,0.1); }
  .info-icon.orange { background: rgba(255,140,66,0.1); }
  .info-card h4 { font-size: 0.92rem; font-weight: 600; color: #fff; }
  .info-card p { font-size: 0.78rem; color: rgba(255,255,255,0.4); margin-top: 2px; }

  .skills-bg { background: linear-gradient(180deg, var(--dark) 0%, var(--dark2) 50%, var(--dark) 100%); }
  .skills-grid { display: grid; grid-template-columns: repeat(auto-fill, minmax(280px, 1fr)); gap: 20px; }
  .skill-card { background: var(--glass); border: 1px solid var(--border); border-radius: 20px; padding: 28px; transition: all 0.4s; position: relative; overflow: hidden; }
  .skill-card::before { content: ''; position: absolute; inset: 0; background: var(--card-grad, linear-gradient(135deg, rgba(0,229,255,0.05), transparent)); opacity: 0; transition: opacity 0.3s; }
  .skill-card:hover::before { opacity: 1; }
  .skill-card:hover { border-color: var(--card-border, rgba(0,229,255,0.3)); transform: translateY(-6px); }
  .skill-card-icon { font-size: 2rem; margin-bottom: 14px; }
  .skill-card h3 { font-family: 'Syne', sans-serif; font-size: 1rem; font-weight: 700; color: #fff; margin-bottom: 8px; }
  .skill-card p { font-size: 0.82rem; color: rgba(255,255,255,0.45); line-height: 1.6; }
  .skill-bar { height: 3px; background: rgba(255,255,255,0.08); border-radius: 100px; margin-top: 16px; }
  .skill-fill { height: 100%; border-radius: 100px; width: 0; transition: width 1.5s cubic-bezier(0.16,1,0.3,1); }
  .skill-fill.visible { width: var(--w); }

  .timeline { position: relative; padding-left: 40px; }
  .timeline::before { content: ''; position: absolute; left: 0; top: 0; bottom: 0; width: 2px; background: linear-gradient(180deg, var(--c1), var(--c5), var(--c2)); border-radius: 100px; }
  .timeline-item { position: relative; margin-bottom: 60px; padding-left: 40px; }
  .timeline-dot { position: absolute; left: -49px; top: 6px; width: 18px; height: 18px; border-radius: 50%; border: 3px solid var(--c1); background: var(--dark); box-shadow: 0 0 20px rgba(0,229,255,0.4); }
  .timeline-dot.purple { border-color: var(--c5); box-shadow: 0 0 20px rgba(168,85,247,0.4); }
  .timeline-dot.green { border-color: var(--c2); box-shadow: 0 0 20px rgba(0,255,148,0.4); }
  .timeline-date { font-family: 'Space Mono', monospace; font-size: 0.72rem; color: var(--c1); letter-spacing: 2px; text-transform: uppercase; margin-bottom: 8px; display: flex; align-items: center; gap: 8px; }
  .now-badge { background: rgba(0,255,148,0.15); color: var(--c2); padding: 2px 10px; border-radius: 100px; font-size: 0.65rem; border: 1px solid rgba(0,255,148,0.3); animation: pulse 2s infinite; }
  .timeline-company { font-family: 'Syne', sans-serif; font-size: 1.4rem; font-weight: 700; color: #fff; }
  .timeline-role { font-size: 0.85rem; color: rgba(255,255,255,0.4); margin-top: 4px; margin-bottom: 16px; }
  .timeline-desc { color: rgba(255,255,255,0.6); font-size: 0.9rem; line-height: 1.8; }
  .timeline-chips { display: flex; flex-wrap: wrap; gap: 8px; margin-top: 16px; }
  .chip { padding: 4px 12px; border-radius: 100px; font-size: 0.72rem; font-family: 'Space Mono', monospace; background: rgba(255,255,255,0.05); color: rgba(255,255,255,0.5); border: 1px solid rgba(255,255,255,0.08); }

  .projects-grid { display: grid; grid-template-columns: repeat(auto-fill, minmax(360px, 1fr)); gap: 24px; }
  .project-card { background: var(--glass); border: 1px solid var(--border); border-radius: 24px; padding: 32px; position: relative; overflow: hidden; transition: all 0.4s; cursor: pointer; }
  .project-card:hover { transform: translateY(-8px); border-color: rgba(255,255,255,0.15); }
  .project-card::after { content: ''; position: absolute; top: 0; left: 0; right: 0; height: 3px; background: var(--card-top, linear-gradient(90deg, var(--c1), var(--c2))); border-radius: 24px 24px 0 0; }
  .project-glow { position: absolute; width: 200px; height: 200px; border-radius: 50%; filter: blur(60px); top: -50px; right: -50px; background: var(--glow-col, var(--c1)); opacity: 0.06; transition: opacity 0.3s; }
  .project-card:hover .project-glow { opacity: 0.12; }
  .project-num { font-family: 'Syne', sans-serif; font-size: 3rem; font-weight: 800; color: rgba(255,255,255,0.04); position: absolute; top: 20px; right: 24px; line-height: 1; }
  .project-icon { font-size: 2rem; margin-bottom: 16px; }
  .project-title { font-family: 'Syne', sans-serif; font-size: 1.15rem; font-weight: 700; color: #fff; margin-bottom: 6px; }
  .project-company { font-size: 0.75rem; color: rgba(255,255,255,0.35); letter-spacing: 1px; text-transform: uppercase; margin-bottom: 14px; font-family: 'Space Mono', monospace; }
  .project-desc { font-size: 0.87rem; color: rgba(255,255,255,0.55); line-height: 1.7; margin-bottom: 18px; }
  .project-tech { display: flex; flex-wrap: wrap; gap: 8px; }
  .project-secret { background: linear-gradient(135deg, rgba(168,85,247,0.1), rgba(0,229,255,0.06)); border-color: rgba(168,85,247,0.25) !important; }
  .secret-badge { display: inline-flex; align-items: center; gap: 6px; background: rgba(168,85,247,0.2); border: 1px solid rgba(168,85,247,0.4); color: var(--c5); padding: 4px 12px; border-radius: 100px; font-size: 0.68rem; font-family: 'Space Mono', monospace; letter-spacing: 1px; margin-bottom: 12px; text-transform: uppercase; animation: pulse 2s infinite; }

  .ai-section { background: linear-gradient(135deg, rgba(168,85,247,0.06), rgba(0,229,255,0.03)); border-top: 1px solid var(--border); border-bottom: 1px solid var(--border); }
  .ai-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 60px; align-items: center; }
  .ai-terminal { background: #0D1117; border: 1px solid rgba(255,255,255,0.08); border-radius: 20px; overflow: hidden; }
  .terminal-header { background: rgba(255,255,255,0.04); padding: 14px 20px; display: flex; align-items: center; gap: 8px; border-bottom: 1px solid rgba(255,255,255,0.06); }
  .tdot { width: 10px; height: 10px; border-radius: 50%; }
  .tdot1 { background: #FF5F57; } .tdot2 { background: #FFBD2E; } .tdot3 { background: #28CA41; }
  .terminal-title { font-family: 'Space Mono', monospace; font-size: 0.7rem; color: rgba(255,255,255,0.3); margin-left: 8px; }
  .terminal-body { padding: 24px; font-family: 'Space Mono', monospace; font-size: 0.78rem; line-height: 2; }
  .t-comment { color: rgba(255,255,255,0.2); }
  .t-prompt { color: var(--c1); }
  .t-key { color: var(--c4); }
  .t-val { color: var(--c2); }
  .t-tag { color: var(--c5); }
  .cursor-blink { animation: blink 1s step-end infinite; }
  @keyframes blink { 0%,100%{opacity:1;} 50%{opacity:0;} }

  .contact-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 60px; }
  .contact-links { display: flex; flex-direction: column; gap: 14px; margin-top: 32px; }
  .contact-item { display: flex; align-items: center; gap: 16px; background: var(--glass); border: 1px solid var(--border); border-radius: 16px; padding: 18px 24px; text-decoration: none; color: #fff; transition: all 0.3s; }
  .contact-item:hover { border-color: var(--item-color, var(--c1)); transform: translateX(8px); }
  .contact-item-icon { width: 40px; height: 40px; border-radius: 10px; display: flex; align-items: center; justify-content: center; font-size: 1.2rem; flex-shrink: 0; background: var(--item-bg, rgba(0,229,255,0.1)); }
  .contact-item span { font-size: 0.85rem; font-family: 'Space Mono', monospace; color: rgba(255,255,255,0.6); }
  .contact-item:hover span { color: rgba(255,255,255,0.9); }

  .big-cta { background: linear-gradient(135deg, rgba(0,229,255,0.08), rgba(0,255,148,0.04)); border: 1px solid rgba(0,229,255,0.2); border-radius: 28px; padding: 50px 40px; text-align: center; position: relative; overflow: hidden; }
  .cta-glow { position: absolute; width: 300px; height: 300px; border-radius: 50%; background: var(--c1); filter: blur(100px); opacity: 0.07; top: 50%; left: 50%; transform: translate(-50%,-50%); animation: blobFloat 5s ease-in-out infinite; }
  .big-cta h3 { font-family: 'Syne', sans-serif; font-size: 2rem; font-weight: 800; color: #fff; margin-bottom: 12px; position: relative; }
  .big-cta p { color: rgba(255,255,255,0.5); margin-bottom: 32px; position: relative; }

  footer { padding: 40px 60px; border-top: 1px solid var(--border); display: flex; align-items: center; justify-content: space-between; position: relative; z-index: 1; }
  footer p { font-family: 'Space Mono', monospace; font-size: 0.72rem; color: rgba(255,255,255,0.2); }

  .scroll-progress { position: fixed; top: 0; left: 0; height: 3px; background: linear-gradient(90deg, var(--c1), var(--c2), var(--c5)); z-index: 200; transition: width 0.1s; }

  .side-nav { position: fixed; right: 28px; top: 50%; transform: translateY(-50%); display: flex; flex-direction: column; gap: 12px; z-index: 100; }
  .side-dot { width: 6px; height: 6px; border-radius: 50%; background: rgba(255,255,255,0.2); cursor: pointer; transition: all 0.3s; }
  .side-dot.active, .side-dot:hover { background: var(--c1); transform: scale(1.5); box-shadow: 0 0 10px rgba(0,229,255,0.5); }

  .marquee-wrap { overflow: hidden; padding: 18px 0; border-top: 1px solid var(--border); border-bottom: 1px solid var(--border); background: rgba(0,229,255,0.02); }
  .marquee-track { display: flex; gap: 60px; animation: marquee 25s linear infinite; width: max-content; }
  .marquee-track:hover { animation-play-state: paused; }
  @keyframes marquee { 0%{transform:translateX(0);} 100%{transform:translateX(-50%);} }
  .marquee-item { display: flex; align-items: center; gap: 10px; font-family: 'Space Mono', monospace; font-size: 0.75rem; color: rgba(255,255,255,0.3); white-space: nowrap; text-transform: uppercase; letter-spacing: 2px; }
  .marquee-item span { color: var(--c1); }

  @media (max-width: 900px) {
    nav { padding: 16px 24px; }
    .nav-links { display: none; }
    .hero { padding: 100px 24px 60px; }
    .views-banner, .phone-frame-float { display: none; }
    .section-wrap { padding: 60px 24px; }
    .about-grid, .ai-grid, .contact-grid { grid-template-columns: 1fr; }
    .projects-grid { grid-template-columns: 1fr; }
    .side-nav { display: none; }
    footer { flex-direction: column; gap: 12px; text-align: center; }
  }
</style>
</head>
<body>

<div class="cursor" id="cursor"></div>
<div class="cursor-ring" id="cursorRing"></div>
<div class="scroll-progress" id="scrollProgress"></div>
<div class="grid-bg"></div>
<div class="blob blob1"></div>
<div class="blob blob2"></div>
<div class="blob blob3"></div>

<div class="side-nav">
  <div class="side-dot active" onclick="gotoSec('#hero')" title="Home"></div>
  <div class="side-dot" onclick="gotoSec('#about')" title="About"></div>
  <div class="side-dot" onclick="gotoSec('#skills')" title="Skills"></div>
  <div class="side-dot" onclick="gotoSec('#experience')" title="Experience"></div>
  <div class="side-dot" onclick="gotoSec('#projects')" title="Projects"></div>
  <div class="side-dot" onclick="gotoSec('#contact')" title="Contact"></div>
</div>

<nav>
  <div class="nav-logo">TK.DEV</div>
  <div class="nav-links">
    <a href="#about">About</a>
    <a href="#skills">Skills</a>
    <a href="#experience">Experience</a>
    <a href="#projects">Projects</a>
    <a href="#contact">Contact</a>
  </div>
  <a href="https://www.linkedin.com/in/tanmay-kundu-897774212/" target="_blank" class="btn-primary" style="padding:10px 22px;font-size:0.78rem;">Connect</a>
</nav>

<!-- HERO -->
<section class="hero" id="hero">
  <div class="hero-tag">
    <div class="tag-dot"></div>
    Available for opportunities
  </div>
  <h1>
    <span class="line1">Tanmay Kundu</span>
    <span class="line2">Android Dev</span>
  </h1>
  <p class="hero-desc">
    Crafting pixel-perfect, high-performance Android & mobile experiences.
    2+ years shipping apps used by thousands — from UPI fintech platforms
    to government tax kiosk machines.
  </p>
  <div class="hero-actions">
    <a href="#projects" class="btn-primary">View Projects</a>
    <a href="https://www.linkedin.com/in/tanmay-kundu-897774212/" target="_blank" class="btn-outline">LinkedIn ↗</a>
  </div>
  <div class="hero-stats">
    <div class="stat-card reveal">
      <div class="stat-val"><span class="count-num" data-target="2">0</span>+</div>
      <div class="stat-label">Years Experience</div>
    </div>
    <div class="stat-card reveal" style="transition-delay:0.1s">
      <div class="stat-val"><span class="count-num" data-target="8">0</span>+</div>
      <div class="stat-label">Apps Shipped</div>
    </div>
    <div class="stat-card reveal" style="transition-delay:0.2s">
      <div class="stat-val"><span class="count-num" data-target="1000">0</span>+</div>
      <div class="stat-label">Daily Active Users</div>
    </div>
    <div class="stat-card reveal" style="transition-delay:0.3s">
      <div class="stat-val"><span class="count-num" data-target="3">0</span></div>
      <div class="stat-label">Platforms</div>
    </div>
  </div>

  <!-- Profile Views -->
  <div class="views-banner">
    <div class="views-row">
      <span style="font-size:1.4rem">👁️</span>
      <div>
        <div class="views-count"><span class="count-num" data-target="2847">0</span></div>
        <div class="views-label">Profile Views</div>
      </div>
    </div>
    <div class="views-live">
      <div class="live-dot"></div>
      <span id="visitCounter">4 visitors right now</span>
    </div>
  </div>

  <!-- Phone mockup -->
  <div class="phone-frame-float">
    <div class="ph-notch"></div>
    <div class="ph-icon">📱</div>
    <div class="ph-label">ANDROID<br>DEVELOPER</div>
    <div class="ph-bar" style="background:linear-gradient(90deg,var(--c1),var(--c2))"></div>
  </div>
</section>

<!-- MARQUEE -->
<div class="marquee-wrap">
  <div class="marquee-track">
    <div class="marquee-item">Kotlin <span>✦</span></div>
    <div class="marquee-item">Jetpack Compose <span>✦</span></div>
    <div class="marquee-item">Flutter <span>✦</span></div>
    <div class="marquee-item">React Native <span>✦</span></div>
    <div class="marquee-item">MVVM <span>✦</span></div>
    <div class="marquee-item">Retrofit REST <span>✦</span></div>
    <div class="marquee-item">Firebase <span>✦</span></div>
    <div class="marquee-item">CI/CD Pipeline <span>✦</span></div>
    <div class="marquee-item">Dagger Hilt <span>✦</span></div>
    <div class="marquee-item">Play Store <span>✦</span></div>
    <div class="marquee-item">POS Integration <span>✦</span></div>
    <div class="marquee-item">Payment Gateways <span>✦</span></div>
    <div class="marquee-item">AI Prompting <span>✦</span></div>
    <div class="marquee-item">Kotlin <span>✦</span></div>
    <div class="marquee-item">Jetpack Compose <span>✦</span></div>
    <div class="marquee-item">Flutter <span>✦</span></div>
    <div class="marquee-item">React Native <span>✦</span></div>
    <div class="marquee-item">MVVM <span>✦</span></div>
    <div class="marquee-item">Retrofit REST <span>✦</span></div>
    <div class="marquee-item">Firebase <span>✦</span></div>
    <div class="marquee-item">CI/CD Pipeline <span>✦</span></div>
    <div class="marquee-item">Dagger Hilt <span>✦</span></div>
    <div class="marquee-item">Play Store <span>✦</span></div>
    <div class="marquee-item">POS Integration <span>✦</span></div>
    <div class="marquee-item">Payment Gateways <span>✦</span></div>
    <div class="marquee-item">AI Prompting <span>✦</span></div>
  </div>
</div>

<!-- ABOUT -->
<section id="about">
  <div class="section-wrap">
    <div class="about-grid">
      <div class="about-text reveal-left">
        <div class="sec-header">
          <div class="sec-eyebrow">About Me</div>
          <h2 class="sec-title">Mobile-first thinker, <span>code-driven</span> builder</h2>
        </div>
        <p>BCA graduate from Pune University with 2+ years of hands-on experience building Android and mobile apps that real people use every day. From fintech UPI platforms processing thousands of transactions, to government kiosk apps for Panvel Municipal Corporation — I build things that matter.</p>
        <p>Currently at Sthapatya Software working on Tax Collection applications for Maharashtra districts. I also maintain Flutter & React Native apps, making me a true multi-platform mobile developer. When I'm not coding, I'm solo travelling and drawing inspiration from the world around me.</p>
        <div class="about-tags">
          <span class="tag tag-cyan">Android</span>
          <span class="tag tag-green">Flutter</span>
          <span class="tag tag-purple">React Native</span>
          <span class="tag tag-yellow">Kotlin</span>
          <span class="tag tag-red">Java</span>
          <span class="tag tag-orange">Jetpack Compose</span>
          <span class="tag tag-cyan">CI/CD</span>
          <span class="tag tag-green">AI Prompting</span>
          <span class="tag tag-purple">Solo Traveller ✈️</span>
        </div>
      </div>
      <div class="about-visual reveal-right">
        <div class="info-card">
          <div class="info-icon cyan">🎓</div>
          <div><h4>BCA — Pune University</h4><p>ASM's CSIT, Pune · CGPA 7.90/10 · 2019–2022</p></div>
        </div>
        <div class="info-card">
          <div class="info-icon green">📍</div>
          <div><h4>Pune, India</h4><p>Open to remote & on-site opportunities</p></div>
        </div>
        <div class="info-card">
          <div class="info-icon purple">🤖</div>
          <div><h4>AI Power User</h4><p>Mastered prompting ChatGPT, Claude & more for 10x dev speed</p></div>
        </div>
        <div class="info-card">
          <div class="info-icon orange">🚀</div>
          <div><h4>Play Store Publisher</h4><p>End-to-end app deployment & management experience</p></div>
        </div>
        <div class="info-card">
          <div class="info-icon cyan">⚙️</div>
          <div><h4>CI/CD Pipeline</h4><p>GitHub Actions, automated builds & deployment workflows</p></div>
        </div>
      </div>
    </div>
  </div>
</section>

<!-- SKILLS -->
<section id="skills" class="skills-bg">
  <div class="section-wrap">
    <div class="sec-header reveal">
      <div class="sec-eyebrow">Technical Skills</div>
      <h2 class="sec-title">My <span>tech</span> arsenal</h2>
    </div>
    <div class="skills-grid">
      <div class="skill-card reveal" style="--card-grad:linear-gradient(135deg,rgba(0,229,255,0.08),transparent);--card-border:rgba(0,229,255,0.3);transition-delay:0s">
        <div class="skill-card-icon">🤖</div>
        <h3>Android Native</h3>
        <p>Kotlin & Java, MVVM, Android SDK, Jetpack libraries, Compose</p>
        <div class="skill-bar"><div class="skill-fill" style="--w:92%;background:linear-gradient(90deg,var(--c1),var(--c2))"></div></div>
      </div>
      <div class="skill-card reveal" style="--card-grad:linear-gradient(135deg,rgba(0,255,148,0.08),transparent);--card-border:rgba(0,255,148,0.3);transition-delay:0.05s">
        <div class="skill-card-icon">💙</div>
        <h3>Flutter</h3>
        <p>Cross-platform Dart development, maintaining production Flutter apps at current org</p>
        <div class="skill-bar"><div class="skill-fill" style="--w:72%;background:linear-gradient(90deg,var(--c2),#00BCD4)"></div></div>
      </div>
      <div class="skill-card reveal" style="--card-grad:linear-gradient(135deg,rgba(168,85,247,0.08),transparent);--card-border:rgba(168,85,247,0.3);transition-delay:0.1s">
        <div class="skill-card-icon">⚛️</div>
        <h3>React Native</h3>
        <p>Cross-platform apps, kiosk development for Panvel Municipal Corp</p>
        <div class="skill-bar"><div class="skill-fill" style="--w:68%;background:linear-gradient(90deg,var(--c5),var(--c1))"></div></div>
      </div>
      <div class="skill-card reveal" style="--card-grad:linear-gradient(135deg,rgba(255,217,61,0.08),transparent);--card-border:rgba(255,217,61,0.3);transition-delay:0.15s">
        <div class="skill-card-icon">💳</div>
        <h3>Payment Integrations</h3>
        <p>Razorpay, Paytm, Pine Labs POS, UPI flows, receipt generation</p>
        <div class="skill-bar"><div class="skill-fill" style="--w:88%;background:linear-gradient(90deg,var(--c4),var(--c6))"></div></div>
      </div>
      <div class="skill-card reveal" style="--card-grad:linear-gradient(135deg,rgba(255,107,107,0.08),transparent);--card-border:rgba(255,107,107,0.3);transition-delay:0.2s">
        <div class="skill-card-icon">🗄️</div>
        <h3>Backend & DB</h3>
        <p>Retrofit REST APIs, Firebase, Room DB, SQLite, Dagger Hilt DI</p>
        <div class="skill-bar"><div class="skill-fill" style="--w:82%;background:linear-gradient(90deg,var(--c3),var(--c6))"></div></div>
      </div>
      <div class="skill-card reveal" style="--card-grad:linear-gradient(135deg,rgba(255,140,66,0.08),transparent);--card-border:rgba(255,140,66,0.3);transition-delay:0.25s">
        <div class="skill-card-icon">⚙️</div>
        <h3>CI/CD Pipeline</h3>
        <p>GitHub Actions, automated testing, Play Store deployment pipelines</p>
        <div class="skill-bar"><div class="skill-fill" style="--w:75%;background:linear-gradient(90deg,var(--c6),var(--c4))"></div></div>
      </div>
      <div class="skill-card reveal" style="--card-grad:linear-gradient(135deg,rgba(168,85,247,0.08),transparent);--card-border:rgba(168,85,247,0.3);transition-delay:0.3s">
        <div class="skill-card-icon">🧠</div>
        <h3>AI Prompt Engineering</h3>
        <p>Mastered ChatGPT, Claude & Gemini to extract production-ready code & architecture decisions</p>
        <div class="skill-bar"><div class="skill-fill" style="--w:90%;background:linear-gradient(90deg,var(--c5),var(--c1))"></div></div>
      </div>
      <div class="skill-card reveal" style="--card-grad:linear-gradient(135deg,rgba(0,229,255,0.08),transparent);--card-border:rgba(0,229,255,0.3);transition-delay:0.35s">
        <div class="skill-card-icon">📐</div>
        <h3>Architecture</h3>
        <p>MVVM, Clean Architecture, multithreading, performance optimization</p>
        <div class="skill-bar"><div class="skill-fill" style="--w:85%;background:linear-gradient(90deg,var(--c2),var(--c5))"></div></div>
      </div>
    </div>
  </div>
</section>

<!-- EXPERIENCE -->
<section id="experience">
  <div class="section-wrap">
    <div class="sec-header reveal">
      <div class="sec-eyebrow">Work History</div>
      <h2 class="sec-title">Where I've <span>built</span> things</h2>
    </div>
    <div class="timeline">
      <div class="timeline-item reveal">
        <div class="timeline-dot"></div>
        <div class="timeline-date" style="color:var(--c2)">Jun 2025 — Present <span class="now-badge">Current</span></div>
        <div class="timeline-company">Sthapatya Software Pvt. Ltd</div>
        <div class="timeline-role">Junior Software Developer · Pune, India</div>
        <div class="timeline-desc">Working on Tax Collection Applications for Maharashtra districts and divisions. Integrated POS machines with payment gateways, built instant receipt generation, and developed a bill scan feature — scan a property tax bill and it auto-loads property details for payment. Also implemented Court Notice / ABC logic, contributing to Flutter & React Native apps alongside Android.</div>
        <div class="timeline-chips">
          <span class="chip">Kotlin</span><span class="chip">Java</span><span class="chip">Flutter</span><span class="chip">React Native</span><span class="chip">POS SDKs</span><span class="chip">Razorpay</span><span class="chip">Pine Labs</span><span class="chip">Paytm</span>
        </div>
      </div>
      <div class="timeline-item reveal">
        <div class="timeline-dot purple"></div>
        <div class="timeline-date" style="color:var(--c5)">Jan 2024 — May 2025</div>
        <div class="timeline-company">Unlock Technologies Pvt. Ltd</div>
        <div class="timeline-role">Android Developer · Mumbai, India</div>
        <div class="timeline-desc">Focused on UPI fintech apps using Kotlin and RESTful API integration. Shipped multiple apps powering 1000+ daily users across train/bus ticketing, utility bill payments, mobile recharges, DTH, FASTag, and secure money transfers. Strong focus on performance optimization and multi-screen UI.</div>
        <div class="timeline-chips">
          <span class="chip">Kotlin</span><span class="chip">MVVM</span><span class="chip">REST APIs</span><span class="chip">UPI</span><span class="chip">Hilt</span><span class="chip">Room DB</span><span class="chip">Retrofit</span>
        </div>
      </div>
      <div class="timeline-item reveal">
        <div class="timeline-dot green"></div>
        <div class="timeline-date" style="color:var(--c2)">Jun 2023 — Nov 2023</div>
        <div class="timeline-company">AppsCodify</div>
        <div class="timeline-role">Android Developer Intern · Remote</div>
        <div class="timeline-desc">Contributed to various Android projects across the full app lifecycle. Gained hands-on experience in Kotlin development, API integration, and Git version control. Learned production-grade development workflows.</div>
        <div class="timeline-chips">
          <span class="chip">Kotlin</span><span class="chip">Git</span><span class="chip">API Integration</span>
        </div>
      </div>
    </div>
  </div>
</section>

<!-- PROJECTS -->
<section id="projects" style="background:linear-gradient(180deg,var(--dark) 0%,var(--dark2) 100%)">
  <div class="section-wrap">
    <div class="sec-header reveal">
      <div class="sec-eyebrow">Projects</div>
      <h2 class="sec-title">Things I've <span>shipped</span></h2>
    </div>
    <div class="projects-grid">
      <div class="project-card reveal" style="--card-top:linear-gradient(90deg,var(--c1),var(--c2));transition-delay:0s">
        <div class="project-glow" style="--glow-col:var(--c1)"></div>
        <div class="project-num">01</div>
        <div class="project-icon">🏛️</div>
        <div class="project-title">Property Tax Kiosk — Panvel Municipal Corp</div>
        <div class="project-company">Sthapatya Software · React Native</div>
        <div class="project-desc">Self-service kiosk app built in React Native. Citizens scan their property tax bill to auto-load property details and pay instantly. Includes Court Notice & ABC logic for flagged properties, full POS payment flow with Pine Labs, Razorpay & Paytm, and receipt printing on success.</div>
        <div class="project-tech">
          <span class="tag tag-cyan">React Native</span>
          <span class="tag tag-yellow">Pine Labs</span>
          <span class="tag tag-green">Razorpay</span>
          <span class="tag tag-orange">Kiosk Mode</span>
          <span class="tag tag-red">Bill Scanner</span>
        </div>
      </div>

      <div class="project-card reveal" style="--card-top:linear-gradient(90deg,var(--c5),var(--c3));transition-delay:0.05s">
        <div class="project-glow" style="--glow-col:var(--c5)"></div>
        <div class="project-num">02</div>
        <div class="project-icon">🚂</div>
        <div class="project-title">Paypoint Retailer</div>
        <div class="project-company">Unlock Technologies · Android</div>
        <div class="project-desc">All-in-one retailer app enabling booking of 1000+ train & bus tickets, utility bill payments, mobile & DTH recharges, FASTag payments, and secure P2P money transfers — serving thousands of daily users across India.</div>
        <div class="project-tech">
          <span class="tag tag-cyan">Kotlin</span>
          <span class="tag tag-purple">MVVM</span>
          <span class="tag tag-green">UPI</span>
          <span class="tag tag-yellow">Retrofit</span>
        </div>
      </div>

      <div class="project-card reveal" style="--card-top:linear-gradient(90deg,var(--c4),var(--c6));transition-delay:0.1s">
        <div class="project-glow" style="--glow-col:var(--c4)"></div>
        <div class="project-num">03</div>
        <div class="project-icon">📊</div>
        <div class="project-title">Paypoint Distributor</div>
        <div class="project-company">Unlock Technologies · Play Store Live ↗</div>
        <div class="project-desc">Management platform for 1000+ distributors of Pay Point India Network. Ledger management, commission tracking, retailer network oversight, and transaction limit configuration.</div>
        <div class="project-tech">
          <span class="tag tag-yellow">Kotlin</span>
          <span class="tag tag-orange">Room DB</span>
          <span class="tag tag-cyan">Hilt</span>
          <span class="tag tag-green">MVVM</span>
        </div>
      </div>

      <div class="project-card reveal" style="--card-top:linear-gradient(90deg,var(--c2),var(--c1));transition-delay:0.15s">
        <div class="project-glow" style="--glow-col:var(--c2)"></div>
        <div class="project-num">04</div>
        <div class="project-icon">💰</div>
        <div class="project-title">Property Tax Collection — POS App</div>
        <div class="project-company">Sthapatya Software · Android</div>
        <div class="project-desc">Android POS app for property tax collection across Maharashtra divisions. Full transaction flow with payment verification, callbacks, and reconciliation. Optimized for POS hardware with instant receipt generation and printing.</div>
        <div class="project-tech">
          <span class="tag tag-cyan">Kotlin/Java</span>
          <span class="tag tag-green">MVVM</span>
          <span class="tag tag-yellow">POS SDKs</span>
          <span class="tag tag-red">REST APIs</span>
        </div>
      </div>

      <div class="project-card project-secret reveal" style="transition-delay:0.2s">
        <div class="project-glow" style="--glow-col:var(--c5)"></div>
        <div class="project-num">05</div>
        <span class="secret-badge">🔒 In Progress</span>
        <div class="project-title">Secret Project Alpha</div>
        <div class="project-company">Personal · Jetpack Compose</div>
        <div class="project-desc">Something big is being built with Jetpack Compose — exploring declarative UI, Compose animations, state management, and Material You design. Details classified. 👀</div>
        <div class="project-tech">
          <span class="tag tag-purple">Jetpack Compose</span>
          <span class="tag tag-cyan">Kotlin</span>
          <span class="tag tag-green">Material You</span>
        </div>
      </div>

      <div class="project-card project-secret reveal" style="transition-delay:0.25s">
        <div class="project-glow" style="--glow-col:var(--c3)"></div>
        <div class="project-num">06</div>
        <span class="secret-badge">🔒 Stealth Mode</span>
        <div class="project-title">Secret Project Beta</div>
        <div class="project-company">Personal · Android + AI</div>
        <div class="project-desc">Combining AI capabilities with mobile development. Leveraging AI prompting mastery to build smarter, more intuitive mobile experiences. Stay tuned. 🚀</div>
        <div class="project-tech">
          <span class="tag tag-red">Compose</span>
          <span class="tag tag-orange">AI Integration</span>
          <span class="tag tag-yellow">Kotlin</span>
        </div>
      </div>
    </div>
  </div>
</section>

<!-- AI PROMPTING -->
<section class="ai-section">
  <div class="section-wrap">
    <div class="ai-grid">
      <div class="reveal-left">
        <div class="sec-eyebrow">Superpower</div>
        <h2 class="sec-title" style="margin-bottom:20px">Mastered <span>AI</span> Prompting</h2>
        <p style="color:rgba(255,255,255,0.5);line-height:1.9;margin-bottom:20px;font-size:0.95rem">In today's dev landscape, knowing how to harness AI tools is a genuine superpower. I've mastered giving precise, context-rich prompts to ChatGPT, Claude, Gemini, and Copilot — extracting production-ready code, architecture decisions, and debugging insights at 10x speed.</p>
        <p style="color:rgba(255,255,255,0.5);line-height:1.9;font-size:0.95rem">This skill lets me ship features faster, tackle unfamiliar tech stacks with confidence, and focus energy on the logic that actually matters.</p>
        <div class="about-tags" style="margin-top:24px">
          <span class="tag tag-purple">ChatGPT</span>
          <span class="tag tag-cyan">Claude</span>
          <span class="tag tag-green">Gemini</span>
          <span class="tag tag-yellow">GitHub Copilot</span>
          <span class="tag tag-orange">Cursor AI</span>
        </div>
      </div>
      <div class="reveal-right">
        <div class="ai-terminal">
          <div class="terminal-header">
            <div class="tdot tdot1"></div>
            <div class="tdot tdot2"></div>
            <div class="tdot tdot3"></div>
            <span class="terminal-title">prompt_engineering.kt</span>
          </div>
          <div class="terminal-body">
            <div><span class="t-comment">// Tanmay's AI Prompting Framework</span></div>
            <div>&nbsp;</div>
            <div><span class="t-key">val</span> <span class="t-val">masterPrompt</span> = buildString {</div>
            <div>&nbsp;&nbsp;<span class="t-tag">context</span>(<span class="t-val">"Android, Kotlin, MVVM"</span>)</div>
            <div>&nbsp;&nbsp;<span class="t-tag">constraints</span>(<span class="t-val">"production-ready"</span>)</div>
            <div>&nbsp;&nbsp;<span class="t-tag">format</span>(<span class="t-val">"code + explanation"</span>)</div>
            <div>&nbsp;&nbsp;<span class="t-tag">examples</span>(<span class="t-val">positive, negative</span>)</div>
            <div>&nbsp;&nbsp;<span class="t-tag">output</span>(<span class="t-val">"step-by-step DSL"</span>)</div>
            <div>}</div>
            <div>&nbsp;</div>
            <div><span class="t-comment">// Result: 10x faster delivery 🚀</span></div>
            <div><span class="t-key">fun</span> <span class="t-val">ship</span>() = masterPrompt.<span class="t-tag">execute</span>()<span class="cursor-blink">▋</span></div>
          </div>
        </div>
      </div>
    </div>
  </div>
</section>

<!-- CONTACT -->
<section id="contact">
  <div class="section-wrap">
    <div class="contact-grid">
      <div class="reveal-left">
        <div class="sec-eyebrow">Get In Touch</div>
        <h2 class="sec-title" style="margin-bottom:20px">Let's <span>build</span> something</h2>
        <p style="color:rgba(255,255,255,0.5);line-height:1.9;font-size:0.95rem">Open to exciting Android / mobile roles, freelance projects, or just a good conversation about tech.</p>
        <div class="contact-links">
          <a href="mailto:tanmayk938@gmail.com" class="contact-item" style="--item-color:var(--c1);--item-bg:rgba(0,229,255,0.1)">
            <div class="contact-item-icon">✉️</div>
            <span>tanmayk938@gmail.com</span>
          </a>
          <a href="https://www.linkedin.com/in/tanmay-kundu-897774212/" target="_blank" class="contact-item" style="--item-color:#0A66C2;--item-bg:rgba(10,102,194,0.1)">
            <div class="contact-item-icon">💼</div>
            <span>linkedin.com/in/tanmay-kundu</span>
          </a>
          <a href="https://github.com/tanmay8830" target="_blank" class="contact-item" style="--item-color:var(--c5);--item-bg:rgba(168,85,247,0.1)">
            <div class="contact-item-icon">🐙</div>
            <span>github.com/tanmay8830</span>
          </a>
          <a href="tel:+918830382482" class="contact-item" style="--item-color:var(--c2);--item-bg:rgba(0,255,148,0.1)">
            <div class="contact-item-icon">📞</div>
            <span>+91 8830382482</span>
          </a>
        </div>
      </div>
      <div class="reveal-right">
        <div class="big-cta">
          <div class="cta-glow"></div>
          <div style="font-size:3rem;margin-bottom:16px;position:relative">🚀</div>
          <h3>Ready to ship great apps?</h3>
          <p>Android, Flutter, or React Native — let's build something users will love.</p>
          <a href="mailto:tanmayk938@gmail.com" class="btn-primary" style="position:relative;display:inline-block">Drop me a message</a>
        </div>
      </div>
    </div>
  </div>
</section>

<footer>
  <p>© 2025 Tanmay Kundu · Built with ❤️ and a lot of Kotlin.</p>
  <p style="color:rgba(255,255,255,0.15)">Android · Flutter · React Native</p>
</footer>

<script>
  // Custom cursor
  const cursor = document.getElementById('cursor');
  const ring = document.getElementById('cursorRing');
  document.addEventListener('mousemove', e => {
    cursor.style.left = e.clientX - 6 + 'px';
    cursor.style.top = e.clientY - 6 + 'px';
    ring.style.left = e.clientX - 18 + 'px';
    ring.style.top = e.clientY - 18 + 'px';
  });
  document.querySelectorAll('a,button,.skill-card,.project-card,.stat-card,.side-dot,.info-card').forEach(el => {
    el.addEventListener('mouseenter', () => { cursor.style.transform='scale(2)'; ring.style.transform='scale(1.5)'; ring.style.borderColor='var(--c2)'; });
    el.addEventListener('mouseleave', () => { cursor.style.transform='scale(1)'; ring.style.transform='scale(1)'; ring.style.borderColor='var(--c1)'; });
  });

  // Scroll progress + side dots
  const prog = document.getElementById('scrollProgress');
  const dots = document.querySelectorAll('.side-dot');
  const sectionIds = ['hero','about','skills','experience','projects','contact'];
  window.addEventListener('scroll', () => {
    prog.style.width = (window.scrollY / (document.body.scrollHeight - window.innerHeight) * 100) + '%';
    sectionIds.forEach((id, i) => {
      const el = document.getElementById(id);
      if (!el) return;
      const r = el.getBoundingClientRect();
      if (r.top <= 200 && r.bottom > 200) { dots.forEach(d => d.classList.remove('active')); if(dots[i]) dots[i].classList.add('active'); }
    });
  });

  // Scroll reveal
  const io = new IntersectionObserver(entries => {
    entries.forEach(e => { if (e.isIntersecting) e.target.classList.add('visible'); });
  }, { threshold: 0.1 });
  document.querySelectorAll('.reveal,.reveal-left,.reveal-right').forEach(el => io.observe(el));

  // Skill bars
  const barObs = new IntersectionObserver(entries => {
    entries.forEach(e => { if (e.isIntersecting) e.target.classList.add('visible'); });
  }, { threshold: 0.3 });
  document.querySelectorAll('.skill-fill').forEach(b => barObs.observe(b));

  // Counter animation
  function animCount(el, target, dur = 2000) {
    let s = 0, inc = target / (dur / 16);
    const t = setInterval(() => {
      s = Math.min(s + inc, target);
      el.textContent = Math.floor(s).toLocaleString();
      if (s >= target) clearInterval(t);
    }, 16);
  }
  const cObs = new IntersectionObserver(entries => {
    entries.forEach(e => {
      if (e.isIntersecting) { animCount(e.target, parseInt(e.target.dataset.target)); cObs.unobserve(e.target); }
    });
  }, { threshold: 0.5 });
  document.querySelectorAll('.count-num').forEach(el => cObs.observe(el));

  // Live visitors
  setInterval(() => {
    const el = document.getElementById('visitCounter');
    if (el) el.textContent = (3 + Math.floor(Math.random() * 4)) + ' visitors right now';
  }, 5000);

  // Section nav
  function gotoSec(id) { document.querySelector(id)?.scrollIntoView({ behavior: 'smooth' }); }

  // 3D tilt on project cards
  document.querySelectorAll('.project-card').forEach(card => {
    card.addEventListener('mousemove', e => {
      const r = card.getBoundingClientRect();
      const x = (e.clientX - r.left) / r.width - 0.5;
      const y = (e.clientY - r.top) / r.height - 0.5;
      card.style.transform = `translateY(-8px) rotateX(${y*-6}deg) rotateY(${x*6}deg)`;
    });
    card.addEventListener('mouseleave', () => { card.style.transform = ''; });
  });

  // Parallax hero text
  window.addEventListener('scroll', () => {
    const h1 = document.querySelector('.hero h1');
    if (h1) h1.style.transform = `translateY(${window.scrollY * 0.12}px)`;
  });
</script>
</body>
</html>
