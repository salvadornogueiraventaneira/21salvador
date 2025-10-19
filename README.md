<!doctype html>
<html lang="pt-PT">
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width,initial-scale=1">
  <title>21 do Salvador — Dedicatórias</title>
  <meta name="description" content="Dedicatórias pessoais — 21 do Salvador (irónico & atrevido)">
  <style>
    :root{--bg:#0b0b0c;--card:#0f1720;--accent:#d4af37;--muted:#9aa4ad;--glass:rgba(255,255,255,0.03)}
    *{box-sizing:border-box}
    html,body{height:100%;margin:0;font-family:Inter, system-ui, -apple-system, 'Segoe UI', Roboto, 'Helvetica Neue', Arial;color:#e6eef6;background:linear-gradient(180deg,#050505 0%, #0b0b0c 60%);}
    .wrap{min-height:100%;display:flex;flex-direction:column;align-items:center;padding:36px}
    header{max-width:900px;width:100%;text-align:center;margin-bottom:18px}
    h1{font-size:28px;letter-spacing:0.6px;margin:6px 0;color:var(--accent)}
    p.lead{color:var(--muted);margin:0 0 18px}

    .card{background:linear-gradient(180deg, rgba(255,255,255,0.02), rgba(255,255,255,0.01));border:1px solid rgba(255,255,255,0.03);backdrop-filter: blur(6px);box-shadow:0 8px 30px rgba(0,0,0,0.6);padding:20px;border-radius:14px;max-width:900px;width:100%}

    .searchRow{display:flex;gap:12px;align-items:center}
    input[type="search"]{flex:1;padding:14px 16px;border-radius:10px;border:1px solid rgba(255,255,255,0.04);background:var(--glass);color:#fff;font-size:16px}
    button.btn{background:var(--accent);border:none;padding:12px 18px;border-radius:10px;color:#071017;font-weight:700;cursor:pointer}
    small.hint{color:var(--muted);display:block;margin-top:8px}

    .result{margin-top:18px;padding:18px;background:#071018;border-radius:12px;border:1px solid rgba(255,255,255,0.02)}
    .name{font-size:20px;color:var(--accent);margin-bottom:8px}
    .msg{color:#e8eef6;line-height:1.5;font-size:16px}

    .notfound{color:#ff6677;font-weight:700}
    .suggestions{margin-top:12px;display:flex;flex-wrap:wrap;gap:8px}
    .chip{padding:8px 12px;border-radius:999px;background:rgba(255,255,255,0.03);border:1px solid rgba(255,255,255,0.02);cursor:pointer}

    footer{max-width:900px;width:100%;margin-top:20px;text-align:center;color:var(--muted);font-size:13px}

    /* playful corner badge */
    .badge{position:fixed;right:18px;bottom:18px;background:var(--accent);color:#071017;padding:10px 14px;border-radius:999px;font-weight:700;box-shadow:0 8px 22px rgba(0,0,0,0.6)}

    @media(max-width:600px){h1{font-size:22px}.searchRow{flex-direction:column;align-items:stretch}button.btn{width:100%}}
  </style>
</head>
<body>
  <div class="wrap">
    <header>
      <h1>21 do Salvador — Dedicatórias</h1>
      <p class="lead">Bem-vindo! Escreve o teu nome abaixo (ou escolhe uma sugestão) para veres a tua dedicatória. Só uma piada, um mimo e pouco drama — tudo a meu cargo.</p>
    </header>

    <main class="card">
      <div class="searchRow">
        <input id="search" type="search" placeholder="Escreve o teu nome... ex: Inês" autocomplete="off" autocapitalize="words" />
        <button id="findBtn" class="btn">Procurar</button>
      </div>
      <small class="hint">Dica: podes escrever apenas parte do nome (ex: 'in' encontra 'Inês').</small>

      <div id="output" class="result" style="display:none" aria-live="polite">
        <div class="name" id="outName"></div>
        <div class="msg" id="outMsg"></div>
      </div>

      <div id="notfound" class="result" style="display:none">
        <div class="notfound">Ops — não encontrei nenhuma dedicatória com esse nome.</div>
        <div class="suggestions" id="suggestions"></div>
      </div>

    </main>

    <footer>
      <div>QR: utiliza o QR do convite para chegar aqui. Se não encontrares o teu nome, experimenta escrever apelidos, diminutivos ou enviar-me mensagem ao vivo.</div>
      <div style="margin-top:6px">21 do Salvador — Edição Icónica • 8 Novembro 2025</div>
    </footer>

    <div class="badge">S21</div>
  </div>

  <script>
    // ====== MENSAGENS ======
    // Substitui as entradas abaixo pelos nomes reais e mensagens que queres.
    // Mantém a estrutura: { name: 'Nome Completo', msg: 'A tua dedicatória...' }
    const messages = [
      { name: 'Nome 1', msg: 'Dedicatória para Nome 1 — escreve aqui a tua mensagem personalizada.' },
      { name: 'Nome 2', msg: 'Dedicatória para Nome 2 — escreve aqui a tua mensagem personalizada.' },
      { name: 'Nome 3', msg: 'Dedicatória para Nome 3 — escreve aqui a tua mensagem personalizada.' },
      { name: 'Nome 4', msg: 'Dedicatória para Nome 4 — escreve aqui a tua mensagem personalizada.' },
      { name: 'Nome 5', msg: 'Dedicatória para Nome 5 — escreve aqui a tua mensagem personalizada.' },
      { name: 'Nome 6', msg: 'Dedicatória para Nome 6 — escreve aqui a tua mensagem personalizada.' },
      { name: 'Nome 7', msg: 'Dedicatória para Nome 7 — escreve aqui a tua mensagem personalizada.' },
      { name: 'Nome 8', msg: 'Dedicatória para Nome 8 — escreve aqui a tua mensagem personalizada.' },
      { name: 'Nome 9', msg: 'Dedicatória para Nome 9 — escreve aqui a tua mensagem personalizada.' },
      { name: 'Nome 10', msg: 'Dedicatória para Nome 10 — escreve aqui a tua mensagem personalizada.' },
      { name: 'Nome 11', msg: 'Dedicatória para Nome 11 — escreve aqui a tua mensagem personalizada.' },
      { name: 'Nome 12', msg: 'Dedicatória para Nome 12 — escreve aqui a tua mensagem personalizada.' },
      { name: 'Nome 13', msg: 'Dedicatória para Nome 13 — escreve aqui a tua mensagem personalizada.' },
      { name: 'Nome 14', msg: 'Dedicatória para Nome 14 — escreve aqui a tua mensagem personalizada.' },
      { name: 'Nome 15', msg: 'Dedicatória para Nome 15 — escreve aqui a tua mensagem personalizada.' },
      { name: 'Nome 16', msg: 'Dedicatória para Nome 16 — escreve aqui a tua mensagem personalizada.' },
      { name: 'Nome 17', msg: 'Dedicatória para Nome 17 — escreve aqui a tua mensagem personalizada.' },
      { name: 'Nome 18', msg: 'Dedicatória para Nome 18 — escreve aqui a tua mensagem personalizada.' },
      { name: 'Nome 19', msg: 'Dedicatória para Nome 19 — escreve aqui a tua mensagem personalizada.' },
      { name: 'Nome 20', msg: 'Dedicatória para Nome 20 — escreve aqui a tua mensagem personalizada.' },
      { name: 'Nome 21', msg: 'Dedicatória para Nome 21 — escreve aqui a tua mensagem personalizada.' },
      { name: 'Nome 22', msg: 'Dedicatória para Nome 22 — escreve aqui a tua mensagem personalizada.' },
      { name: 'Nome 23', msg: 'Dedicatória para Nome 23 — escreve aqui a tua mensagem personalizada.' },
      { name: 'Nome 24', msg: 'Dedicatória para Nome 24 — escreve aqui a tua mensagem personalizada.' },
      { name: 'Nome 25', msg: 'Dedicatória para Nome 25 — escreve aqui a tua mensagem personalizada.' },
      { name: 'Nome 26', msg: 'Dedicatória para Nome 26 — escreve aqui a tua mensagem personalizada.' },
      { name: 'Nome 27', msg: 'Dedicatória para Nome 27 — escreve aqui a tua mensagem personalizada.' },
      { name: 'Nome 28', msg: 'Dedicatória para Nome 28 — escreve aqui a tua mensagem personalizada.' },
      { name: 'Nome 29', msg: 'Dedicatória para Nome 29 — escreve aqui a tua mensagem personalizada.' },
      { name: 'Nome 30', msg: 'Dedicatória para Nome 30 — escreve aqui a tua mensagem personalizada.' },
      { name: 'Nome 31', msg: 'Dedicatória para Nome 31 — escreve aqui a tua mensagem personalizada.' },
      { name: 'Nome 32', msg: 'Dedicatória para Nome 32 — escreve aqui a tua mensagem personalizada.' },
      { name: 'Nome 33', msg: 'Dedicatória para Nome 33 — escreve aqui a tua mensagem personalizada.' },
      { name: 'Nome 34', msg: 'Dedicatória para Nome 34 — escreve aqui a tua mensagem personalizada.' },
      { name: 'Nome 35', msg: 'Dedicatória para Nome 35 — escreve aqui a tua mensagem personalizada.' },
      { name: 'Nome 36', msg: 'Dedicatória para Nome 36 — escreve aqui a tua mensagem personalizada.' },
      { name: 'Nome 37', msg: 'Dedicatória para Nome 37 — escreve aqui a tua mensagem personalizada.' },
      { name: 'Nome 38', msg: 'Dedicatória para Nome 38 — escreve aqui a tua mensagem personalizada.' },
      { name: 'Nome 39', msg: 'Dedicatória para Nome 39 — escreve aqui a tua mensagem personalizada.' },
      { name: 'Nome 40', msg: 'Dedicatória para Nome 40 — escreve aqui a tua mensagem personalizada.' },
      { name: 'Nome 41', msg: 'Dedicatória para Nome 41 — escreve aqui a tua mensagem personalizada.' },
      { name: 'Nome 42', msg: 'Dedicatória para Nome 42 — escreve aqui a tua mensagem personalizada.' },
      { name: 'Nome 43', msg: 'Dedicatória para Nome 43 — escreve aqui a tua mensagem personalizada.' },
      { name: 'Nome 44', msg: 'Dedicatória para Nome 44 — escreve aqui a tua mensagem personalizada.' },
      { name: 'Nome 45', msg: 'Dedicatória para Nome 45 — escreve aqui a tua mensagem personalizada.' },
      { name: 'Nome 46', msg: 'Dedicatória para Nome 46 — escreve aqui a tua mensagem personalizada.' },
      { name: 'Nome 47', msg: 'Dedicatória para Nome 47 — escreve aqui a tua mensagem personalizada.' },
      { name: 'Nome 48', msg: 'Dedicatória para Nome 48 — escreve aqui a tua mensagem personalizada.' },
      { name: 'Nome 49', msg: 'Dedicatória para Nome 49 — escreve aqui a tua mensagem personalizada.' },
      { name: 'Nome 50', msg: 'Dedicatória para Nome 50 — escreve aqui a tua mensagem personalizada.' },
      { name: 'Nome 51', msg: 'Dedicatória para Nome 51 — escreve aqui a tua mensagem personalizada.' }
    ];

    // ====== UTIL HELPERS ======
    function normalize(s){
      return s.normalize('NFD').replace(/\p{Diacritic}/gu,'').toLowerCase().trim();
    }

    // find exact or partial matches
    function findMatches(query){
      const q = normalize(query);
      if(!q) return [];
      // exact first
      let exact = messages.find(m => normalize(m.name)===q);
      if(exact) return [exact];
      // partial matches
      const partials = messages.filter(m => normalize(m.name).includes(q));
      // fuzzy fallback: includes initials match
      if(partials.length>0) return partials;
      // initials match (e.g. 'JS' find 'Joao Silva')
      const initials = messages.filter(m => {
        const inits = m.name.split(/\s+/).map(p=>p[0]||'').join('').toLowerCase();
        return inits.includes(q.replace(/\s+/g,''));
      });
      return initials;
    }

    // ====== UI ======
    const search = document.getElementById('search');
    const findBtn = document.getElementById('findBtn');
    const output = document.getElementById('output');
    const outName = document.getElementById('outName');
    const outMsg = document.getElementById('outMsg');
    const notfound = document.getElementById('notfound');
    const suggestions = document.getElementById('suggestions');

    function showMessage(obj){
      outName.textContent = obj.name;
      outMsg.innerHTML = obj.msg.replace(/\n/g,'<br>');
      notfound.style.display='none';
      output.style.display='block';
    }

    function showNotFound(q, matches){
      output.style.display='none';
      suggestions.innerHTML='';
      if(matches && matches.length){
        matches.slice(0,10).forEach(m=>{
          const c = document.createElement('div');c.className='chip';c.textContent=m.name;c.onclick=()=>{search.value=m.name; performFind();};suggestions.appendChild(c);
        });
        notfound.style.display='block';
        return;
      }
      notfound.style.display='block';
    }

    function performFind(){
      const q = search.value;
      const results = findMatches(q);
      if(results.length===1){
        showMessage(results[0]);
      } else if(results.length>1){
        // show first result preview and suggestions
        showNotFound(q, results);
      } else {
        showNotFound(q, []);
      }
    }

    findBtn.addEventListener('click', performFind);
    search.addEventListener('keydown', function(e){ if(e.key==='Enter'){ performFind(); } });

    // if URL has ?name= query parameter, auto-fill and open
    (function(){
      const params = new URLSearchParams(window.location.search);
      const name = params.get('name');
      if(name){ search.value = name; performFind(); }
    })();

    // Accessibility: focus input on load
    window.addEventListener('load', ()=>{search.focus();});
  </script>
</body>
</html>
