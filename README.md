<!doctype html>
<html lang="en">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width,initial-scale=1" />
  <title>DocuBot — RAG-based AI Chatbot</title>
  <style>
    /* --- Page layout --- */
    :root{
      --bg:#0f1724; /* dark slate */
      --card:#0b1220;
      --muted:#9aa8bf;
      --accent:#4f46e5;
      --accent-2:#06b6d4;
      --glass: rgba(255,255,255,0.03);
      --radius:12px;
      --mono: "Segoe UI", Roboto, "Helvetica Neue", Arial, sans-serif;
    }
    html,body{height:100%; margin:0; font-family:var(--mono); background:linear-gradient(180deg,#071028 0%, #082033 100%); color:#e6eef8;}
    .container{max-width:980px; margin:36px auto; padding:28px; background:linear-gradient(180deg, rgba(255,255,255,0.02), rgba(255,255,255,0.01)); border-radius:16px; box-shadow: 0 8px 30px rgba(2,6,23,0.6); border:1px solid rgba(255,255,255,0.03);}
    header{display:flex; align-items:center; gap:16px;}
    .logo{width:72px; height:72px; border-radius:12px; background:linear-gradient(90deg,var(--accent),var(--accent-2)); display:flex; align-items:center; justify-content:center; font-weight:700; font-size:22px; color:white;}
    h1{margin:0; font-size:26px;}
    p.lead{margin:6px 0 0; color:var(--muted);}

    /* badges */
    .badges{margin-top:14px; display:flex; gap:8px; flex-wrap:wrap;}
    .badge{background:var(--glass); padding:6px 10px; border-radius:8px; font-size:13px; color:var(--muted); border:1px solid rgba(255,255,255,0.02);}

    /* sections */
    section{margin-top:22px;}
    .grid{display:grid; grid-template-columns:1fr 320px; gap:20px;}
    .card{background:linear-gradient(180deg, rgba(255,255,255,0.01), rgba(255,255,255,0.00)); padding:18px; border-radius:12px; border:1px solid rgba(255,255,255,0.02);}
    .muted{color:var(--muted); font-size:14px;}
    ul.features{padding-left:18px; margin:8px 0 0;}
    ul.features li{margin:8px 0;}

    code, pre{background:rgba(0,0,0,0.25); padding:6px 8px; border-radius:6px; color:#cfe7ff; font-size:13px;}
    pre{overflow:auto; max-height:280px; padding:12px; margin:10px 0; border-left:4px solid rgba(255,255,255,0.03);}

    /* project structure */
    .tree{font-family:monospace; color:#cfe7ff; background:linear-gradient(180deg, rgba(255,255,255,0.01), rgba(255,255,255,0.00)); padding:12px; border-radius:8px; border:1px dashed rgba(255,255,255,0.03);}

    /* buttons and links */
    a.btn{display:inline-block; background:var(--accent); color:white; padding:8px 12px; border-radius:10px; text-decoration:none; font-weight:600;}
    a.ghost{background:transparent; border:1px solid rgba(255,255,255,0.04); color:var(--muted); padding:8px 10px; border-radius:10px; text-decoration:none; }

    /* screenshots & video */
    .media{display:flex; flex-direction:column; gap:10px;}
    .screenshot{width:100%; height:160px; border-radius:8px; background:linear-gradient(180deg, rgba(255,255,255,0.02), rgba(255,255,255,0.01)); display:flex; align-items:center; justify-content:center; color:var(--muted); border:1px dashed rgba(255,255,255,0.03); font-size:13px;}
    .video-thumb{width:100%; border-radius:8px; overflow:hidden; border:1px solid rgba(255,255,255,0.03);}

    footer{margin-top:26px; color:var(--muted); font-size:13px; display:flex; justify-content:space-between; align-items:center;}
    @media (max-width:920px){ .grid{grid-template-columns:1fr; } .card{padding:14px;} .container{margin:16px; padding:16px;} }
  </style>
</head>
<body>
  <div class="container" role="main">
    <header>
      <div class="logo">DB</div>
      <div>
        <h1>DocuBot <span style="font-size:14px; color:var(--muted); font-weight:600;">— RAG-based AI Chatbot (developer-focused)</span></h1>
        <p class="lead">Retrieval-Augmented Generation pipeline using <strong>React</strong>, <strong>Node.js</strong>, <strong>LangChain</strong>, <strong>Qdrant</strong>, and <strong>Google Gemini</strong>. Enhances prompts, retrieves semantic chunks, and generates grounded answers.</p>

        <div class="badges" aria-hidden="true">
          <div class="badge">Frontend: React</div>
          <div class="badge">Backend: Node.js</div>
          <div class="badge">Orchestration: LangChain</div>
          <div class="badge">VectorDB: Qdrant</div>
          <div class="badge">LLM: Gemini</div>
          <div class="badge">License: MIT</div>
        </div>
      </div>
    </header>

    <section class="grid" aria-labelledby="features-heading">
      <div>
        <div class="card">
          <h2 id="features-heading" style="margin-top:0;">🚀 Key Features</h2>
          <ul class="features">
            <li><strong>Advanced RAG pipeline</strong>: prompt enhancement → retrieval → grounded generation.</li>
            <li><strong>Prompt Enhancer</strong>: rewrite & normalize queries to improve retrieval recall.</li>
            <li><strong>Semantic retrieval</strong> with Qdrant (top-k chunk search).</li>
            <li><strong>PDF ingestion</strong>: chunking + embeddings using LangChain loaders.</li>
            <li><strong>Modular backend</strong>: services, controllers, routes, utils, db, middleware for easy extension.</li>
          </ul>
        </div>

        <div class="card" style="margin-top:16px;">
          <h3 style="margin:0 0 8px 0;">🏗️ Tech Stack</h3>
          <p class="muted" style="margin:0 0 8px 0;">React, Node.js, Express, LangChain, Qdrant, Google Generative AI (Gemini), GoogleGenerativeAIEmbeddings.</p>

          <h4 style="margin:12px 0 6px 0;">Project Structure</h4>
          <div class="tree">
<pre style="margin:0; font-size:13px;">
DocuBot/
├─ frontend/                 # React app (UI)
├─ backend/                  # Node + Express
│  ├─ controllers/           # HTTP handlers (thin)
│  ├─ services/              # Business logic (RAG, embeddings, AI calls)
│  ├─ routes/                # Route definitions
│  ├─ db/                    # Qdrant client & helpers
│  ├─ utils/                 # Prompt builders, LangChain helpers
│  ├─ middleware/            # Auth, error handling, logging
│  ├─ app.js                 # Express app setup
│  └─ server.js              # HTTP server bootstrap
├─ uploads/                  # Uploaded files (PDFs)
├─ screenshots/              # Add screenshots here
└─ README.html
</pre>
          </div>
        </div>

        <div class="card" style="margin-top:16px;">
          <h3 style="margin:0 0 8px 0;">⚙️ Installation (quick)</h3>
          <ol style="color:var(--muted); margin:0 0 12px 18px;">
            <li>Clone repo: <code>git clone https://github.com/your-username/DocuBot.git</code></li>
            <li>Backend: <code>cd backend && npm install</code></li>
            <li>Set `.env` (see example below).</li>
            <li>Start backend: <code>npm run dev</code>.</li>
            <li>Frontend: <code>cd ../frontend && npm install && npm start</code>.</li>
          </ol>

          <strong style="display:block; margin-top:8px;">Example `.env`</strong>
          <pre>PORT=8080
QDRANT_URL=http://localhost:6333
QDRANT_COLLECTION=docubot_collection
GOOGLE_API_KEY=your_google_api_key
GENAI_BASE_URI=https://generativelanguage.googleapis.com/v1beta/openai
FRONTEND_URL=http://localhost:3000
NODE_ENV=development
</pre>
        </div>

      </div>

      <aside>
        <div class="card">
          <h3 style="margin:0 0 12px 0;">🔍 How it works</h3>
          <ol style="color:var(--muted); margin:0 0 12px 18px;">
            <li>Ingest: PDF → chunk → embed → store in Qdrant.</li>
            <li>Enhance: user query rewritten (LLM) to increase retrieval quality.</li>
            <li>Retrieve: semantic search (top-k) returning relevant chunks.</li>
            <li>Answer: LLM generates response grounded on retrieved context.</li>
          </ol>

          <h4 style="margin-top:8px;">API Quick Examples</h4>
          <div class="muted" style="font-size:13px;">
            <strong>Upload file</strong><br>
            <code>curl -X POST http://localhost:8080/api/files/upload -F "file=@/path/file.pdf"</code>
            <br><br>
            <strong>Chat / RAG query</strong><br>
            <code>curl -X POST http://localhost:8080/api/chat -H "Content-Type: application/json" -d '{ "query":"Summarize section 2","fileName":"file.pdf" }'</code>
            <br><br>
            <strong>Delete vectors</strong><br>
            <code>curl -X DELETE http://localhost:8080/api/files/file.pdf</code>
          </div>

          <div style="margin-top:12px;">
            <a class="btn" href="https://github.com/your-username/DocuBot" target="_blank" rel="noopener">View on GitHub</a>
            <a class="ghost" href="#" style="margin-left:8px;">Open API docs</a>
          </div>
        </div>

        <div class="card" style="margin-top:16px;">
          <h3 style="margin:0 0 8px 0;">📂 Screenshots & Demo</h3>
          <div class="media">
            <div class="screenshot">Add: <code>./screenshots/home.png</code> (Home page)</div>
            <div class="screenshot">Add: <code>./screenshots/upload.png</code> (Upload flow)</div>
            <div class="screenshot">Add: <code>./screenshots/chat.png</code> (Chat interface)</div>

            <div style="margin-top:10px;">
              <h4 style="margin:0 0 8px 0;">🎥 Demo video</h4>
              <!-- Replace VIDEO_ID with your YouTube video id -->
              <a class="video-thumb" href="https://www.youtube.com/watch?v=VIDEO_ID" target="_blank" rel="noopener">
                <img style="display:block; width:100%;" src="https://img.youtube.com/vi/VIDEO_ID/0.jpg" alt="DocuBot demo thumbnail" />
              </a>
              <div style="color:var(--muted); font-size:13px; margin-top:8px;">
                Replace <code>VIDEO_ID</code> with your uploaded YouTube video's ID.
              </div>
            </div>
          </div>
        </div>
      </aside>
    </section>

    <section class="card" style="margin-top:20px;">
      <h3 style="margin-top:0;">📌 Roadmap</h3>
      <ul class="features">
        <li>Support DOCX / MD ingestion and automatic OCR</li>
        <li>Streaming LLM responses + token-level highlights</li>
        <li>Docker + k8s deployment & infra templates</li>
        <li>Per-user sessions, multi-tenant support, and auth</li>
      </ul>
    </section>

    <section class="card" style="margin-top:16px;">
      <h3 style="margin-top:0;">🤝 Contributing</h3>
      <p class="muted">Contributions welcome — open an issue or submit a pull request. Please follow the existing code style and include tests for new features.</p>
      <p class="muted"><strong>Suggested branches:</strong> <code>main</code> (stable), <code>dev</code> (work-in-progress).</p>
    </section>

    <footer>
      <div>MIT © 2025 — <a href="https://github.com/your-username/DocuBot" style="color:inherit; text-decoration:underline;">your-username/DocuBot</a></div>
      <div class="muted">Built with LangChain • Qdrant • Gemini</div>
    </footer>
  </div>
</body>
</html>
