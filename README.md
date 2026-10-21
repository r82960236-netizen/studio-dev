<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Studio Devs</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', system-ui, -apple-system, sans-serif;
        }

        body {
            background-color: #0b0f19;
            color: #ffffff;
            min-height: 100vh;
            padding: 15px;
            display: flex;
            flex-direction: column;
            align-items: center;
        }

        .header-container {
            width: 100%;
            max-width: 450px;
            position: relative;
            text-align: center;
            margin-bottom: 12px;
        }

        .header h1 {
            font-size: 1.6rem;
            color: #00ff88;
            font-weight: 700;
        }

        .header p {
            font-size: 0.85rem;
            color: #94a3b8;
            margin-top: 2px;
        }

        .creator-info {
            font-size: 0.8rem;
            color: #38bdf8;
            margin-top: 4px;
        }

        .admin-btn {
            position: absolute;
            right: 0;
            top: 5px;
            background: none;
            border: none;
            color: #94a3b8;
            font-size: 1.4rem;
            cursor: pointer;
            z-index: 10;
        }

        .admin-btn:hover {
            color: #00ff88;
        }

        .stats-bar {
            width: 100%;
            max-width: 450px;
            background: #131b2e;
            border: 1px solid rgba(255, 255, 255, 0.08);
            border-radius: 12px;
            padding: 10px 15px;
            display: flex;
            justify-content: space-around;
            margin-bottom: 12px;
            font-size: 0.82rem;
            color: #cbd5e1;
        }

        .stat-item {
            display: flex;
            align-items: center;
            gap: 6px;
        }

        .status-dot {
            width: 8px;
            height: 8px;
            background-color: #22c55e;
            border-radius: 50%;
            box-shadow: 0 0 8px #22c55e;
        }

        .search-box {
            width: 100%;
            max-width: 450px;
            margin-bottom: 15px;
            position: relative;
        }

        .search-box input {
            width: 100%;
            padding: 12px 16px 12px 40px;
            border-radius: 12px;
            border: 1px solid rgba(255, 255, 255, 0.1);
            background: #131b2e;
            color: #fff;
            outline: none;
            font-size: 0.9rem;
        }

        .search-icon {
            position: absolute;
            left: 14px;
            top: 50%;
            transform: translateY(-50%);
            color: #94a3b8;
        }

        .category-bar {
            width: 100%;
            max-width: 450px;
            display: flex;
            gap: 8px;
            margin-bottom: 20px;
            overflow-x: auto;
            padding-bottom: 5px;
        }

        .category-bar::-webkit-scrollbar {
            display: none;
        }

        .cat-btn {
            background: #131b2e;
            border: 1px solid rgba(255, 255, 255, 0.08);
            color: #94a3b8;
            padding: 8px 16px;
            border-radius: 20px;
            font-size: 0.85rem;
            font-weight: 600;
            cursor: pointer;
            white-space: nowrap;
            transition: all 0.2s;
        }

        .cat-btn.active {
            background: #00ffaa;
            color: #000000;
            border-color: #00ffaa;
            font-weight: 700;
        }

        .cat-btn.vip-tab {
            border-color: #fde047;
            color: #fde047;
        }

        .cat-btn.vip-tab.active {
            background: linear-gradient(135deg, #eab308, #ca8a04);
            color: #fff;
        }

        .section-title {
            width: 100%;
            max-width: 450px;
            font-size: 1rem;
            color: #00ff88;
            margin-bottom: 12px;
            display: flex;
            align-items: center;
            gap: 6px;
        }

        .container {
            width: 100%;
            max-width: 450px;
            display: flex;
            flex-direction: column;
            gap: 16px;
        }

        .card {
            background: #131b2e;
            border: 1px solid rgba(255, 255, 255, 0.08);
            border-radius: 16px;
            overflow: hidden;
            box-shadow: 0 4px 12px rgba(0, 0, 0, 0.3);
            position: relative;
        }

        .card-img-container {
            position: relative;
            width: 100%;
            height: 180px;
            background: #0b0f19;
        }

        .card-img {
            width: 100%;
            height: 100%;
            object-fit: cover;
        }

        .demand-badge {
            position: absolute;
            top: 10px;
            right: 10px;
            background: rgba(15, 23, 42, 0.85);
            border: 1px solid rgba(255, 255, 255, 0.15);
            color: #00ffaa;
            font-size: 0.7rem;
            font-weight: 700;
            padding: 4px 10px;
            border-radius: 20px;
            display: flex;
            align-items: center;
            gap: 4px;
        }

        .card-body {
            padding: 14px;
        }

        .card-title {
            font-size: 1.05rem;
            font-weight: 700;
            color: #ffffff;
            margin-bottom: 4px;
            line-height: 1.3;
        }

        .card-desc {
            font-size: 0.85rem;
            color: #94a3b8;
            margin-bottom: 10px;
            line-height: 1.4;
        }

        .card-author {
            font-size: 0.82rem;
            color: #38bdf8;
            margin-bottom: 12px;
            display: flex;
            align-items: center;
            gap: 6px;
        }

        .card-footer {
            display: flex;
            gap: 8px;
            align-items: center;
            background: #0b0f19;
            padding: 10px 12px;
            border-radius: 10px;
            border: 1px solid rgba(255, 255, 255, 0.05);
        }

        .id-text {
            flex: 1;
            font-family: monospace;
            font-size: 0.82rem;
            color: #00ffaa;
            overflow: hidden;
            text-overflow: ellipsis;
            white-space: nowrap;
        }

        .btn-copy {
            background: #00ffaa;
            color: #000000;
            border: none;
            padding: 6px 14px;
            border-radius: 8px;
            font-weight: 700;
            font-size: 0.82rem;
            cursor: pointer;
            transition: transform 0.1s;
        }

        .btn-copy:active {
            transform: scale(0.95);
        }

        .copyright-footer {
            width: 100%;
            max-width: 450px;
            text-align: center;
            margin-top: 30px;
            padding: 15px;
            font-size: 0.75rem;
            color: #64748b;
            border-top: 1px solid rgba(255, 255, 255, 0.05);
        }

        .modal {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0, 0, 0, 0.85);
            justify-content: center;
            align-items: center;
            z-index: 100;
            padding: 15px;
        }

        .modal-content {
            background: #131b2e;
            border: 1px solid rgba(255, 255, 255, 0.1);
            border-radius: 16px;
            width: 100%;
            max-width: 420px;
            padding: 20px;
            max-height: 90vh;
            overflow-y: auto;
        }

        .modal-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 15px;
        }

        .form-group {
            margin-bottom: 12px;
            text-align: left;
        }

        .form-group label {
            display: block;
            font-size: 0.8rem;
            color: #94a3b8;
            margin-bottom: 4px;
        }

        .form-group input, .form-group select, .form-group textarea {
            width: 100%;
            padding: 10px;
            border-radius: 8px;
            border: 1px solid rgba(255, 255, 255, 0.1);
            background: #0b0f19;
            color: #fff;
            outline: none;
        }

        .btn-submit {
            width: 100%;
            background: #00ffaa;
            color: #000;
            border: none;
            padding: 10px;
            border-radius: 8px;
            font-weight: 700;
            cursor: pointer;
            margin-top: 10px;
        }

        .divider {
            border: 0;
            height: 1px;
            background: rgba(255, 255, 255, 0.1);
            margin: 15px 0;
        }
    </style>
        <script>
        let selectedCategory = 'todos';
        
        let initialKits = [
            {
                categoria: "kit",
                altaDemanda: true,
                creador: "Estudio Dev",
                id: "118731072483615",
                portada: "https://images.unsplash.com/photo-1618005182384-a83a8bd57fbe?auto=format&fit=crop&w=400&q=80",
                nombre: "Sistema de Boss para Roblox",
                descripcion: "Increíble sistema de boss completo con barras de vida, fases de batalla y mecánicas listas para usar."
            },
            {
                categoria: "kit",
                altaDemanda: true,
                creador: "Devfran (TikTok)",
                id: "95870844492917",
                portada: "https://i.ibb.co/f3XBv72/IMG-6cf8deb8-a44f-4610-b046-c11a6ab34d6a.jpg",
                nombre: "Kit de Roba un Brainrot",
                descripcion: "Espero que lo disfrutes y puedas personalizar tu juego."
            },
            {
                categoria: "modelo",
                altaDemanda: false,
                creador: "@RbxlProductInc (Roblox)",
                id: "90402705071528",
                portada: "https://i.ibb.co/vxyxHdp3/Meta-AI-856174133-1483537224119190-1708194579167308606-n-20261021-011102.jpg",
                nombre: "Decoración de Halloween",
                descripcion: "Elementos temáticos para tus eventos de terror en el juego."
            },
            {
                categoria: "kit",
                altaDemanda: false,
                creador: "@kiwirblxx (YouTube)",
                id: "127823029091052",
                portada: "https://images.unsplash.com/photo-1618005182384-a83a8bd57fbe?auto=format&fit=crop&w=400&q=80",
                nombre: "Steal an Egg Kit v8",
                descripcion: "Like and subscribe! Steal a egg kit v8 next!!!"
            },
            {
                categoria: "kit",
                altaDemanda: true,
                creador: "PurlyDev",
                id: "9750178951",
                portada: "https://i.ibb.co/spPNBJCd/Screenshot-2026-10-21-01-26-30-156-com-google-android-youtube-edit.jpg",
                nombre: "Free FPS KIT V1",
                descripcion: "Sistema de disparo en primera persona totalmente optimizado."
            },
            {
                categoria: "kit",
                altaDemanda: false,
                creador: "Desconocido",
                id: "75591328222136",
                portada: "https://i.ibb.co/S7vjXQrm/Screenshot-2026-10-21-01-30-51-481-com-google-android-youtube-edit.jpg",
                nombre: "Kit de Planta un Jardín",
                descripcion: "Crea tu propio juego de granja o jardín con este kit modular."
            },
            {
                categoria: "kit",
                altaDemanda: false,
                creador: "Desconocido",
                id: "88508791265667",
                portada: "https://i.ibb.co/M5ydK5kJ/Screenshot-2026-10-21-01-37-58-816-com-google-android-youtube-edit.jpg",
                nombre: "Kit de Raivlas",
                descripcion: "Mecánicas listas y configurables para tu proyecto."
            },
            {
                categoria: "kit",
                altaDemanda: false,
                creador: "Desconocido",
                id: "122214542643927",
                portada: "https://i.ibb.co/q3TXcLGM/Screenshot-2026-10-21-01-48-32-505-com-google-android-youtube-edit.jpg",
                nombre: "Creador de Avatar Style",
                descripcion: "Interfaz personalizada para la edición de personajes."
            },
            {
                categoria: "kit",
                altaDemanda: false,
                creador: "Desconocido",
                id: "110679090556362",
                portada: "https://i.ibb.co/R4j21SLh/IMG-63ae6506-9034-49fc-a154-11a8fa89e191.jpg",
                nombre: "Plants vs. Brainrots Kit",
                descripcion: "¿Quieres crear tu propio juego inspirado en Plants vs. Brainrots en Roblox?"
            },
            {
                categoria: "kit",
                altaDemanda: false,
                creador: "Desconocido",
                id: "132694563019063",
                portada: "https://i.ibb.co/m51cNqgB/Screenshot-2026-10-21-01-51-00-593-com-google-android-youtube-edit.jpg",
                nombre: "CMRDR Kit",
                descripcion: "Kit con herramientas avanzadas para tu mapa."
            },
            {
                categoria: "kit",
                altaDemanda: false,
                creador: "Desconocido",
                id: "12207014022",
                portada: "https://i.ibb.co/kVhfYW3W/Screenshot-2026-10-21-01-53-01-540-com-google-android-youtube-edit.jpg",
                nombre: "Sistema de Fútbol",
                descripcion: "Mecánicas de balón, porterías y marcador automático."
            },
            {
                categoria: "kit",
                altaDemanda: true,
                creador: "hernan_16267 (TikTok)",
                id: "89911848961264",
                portada: "https://i.ibb.co/wrhhJzCd/Screenshot-2026-10-21-11-38-06-954-com-lemon-lvoverseas-edit.jpg",
                nombre: "Sistema de Tags",
                descripcion: "Sistema de etiquetas para tu juego con distintas interfaces y buenas GUIs."
            }
        ];

        let kits = JSON.parse(localStorage.getItem('studioDevs_items_v16')) || initialKits;
        let downloadCount = localStorage.getItem('studioDevs_downloads') ? parseInt(localStorage.getItem('studioDevs_downloads')) : 1248;

        function renderKits(items) {
            const container = document.getElementById('kitsContainer');
            if(!container) return;
            container.innerHTML = '';

            if (items.length === 0) {
                container.innerHTML = '<p style="text-align:center; color:#94a3b8; padding:20px;">No se encontraron resultados.</p>';
                return;
            }

            items.forEach((item) => {
                const imgUrl = item.portada && item.portada.startsWith('http') ? item.portada : 'https://images.unsplash.com/photo-1618005182384-a83a8bd57fbe?auto=format&fit=crop&w=400&q=80';
                const altaBadge = item.altaDemanda ? '<div class="demand-badge">🔥 Alta Demanda</div>' : '';
                const itemNombre = item.nombre ? item.nombre : item.descripcion;
                const itemDesc = item.descripcion && item.nombre ? `<div class="card-desc">${item.descripcion}</div>` : '';

                const cardHtml = `
                    <div class="card">
                        <div class="card-img-container">
                            <img src="${imgUrl}" class="card-img" alt="Portada">
                            ${altaBadge}
                        </div>
                        <div class="card-body">
                            <div class="card-title">${itemNombre}</div>
                            ${itemDesc}
                            <div class="card-author">👤 Creador: ${item.creador}</div>
                            <div class="card-footer">
                                <span class="id-text">ID: ${item.id}</span>
                                <button class="btn-copy" onclick="copyId('${item.id}')">Copiar ID</button>
                            </div>
                        </div>
                    </div>
                `;
                container.innerHTML += cardHtml;
            });
        }

        function copyId(id) {
            navigator.clipboard.writeText(id);
            downloadCount++;
            localStorage.setItem('studioDevs_downloads', downloadCount);
            document.getElementById('download-count').innerText = downloadCount.toLocaleString();
            alert('¡ID copiado al portapapeles! 📥 Descarga registrada.');
        }

        function selectCategory(cat, btnElement) {
            selectedCategory = cat;
            document.querySelectorAll('.cat-btn').forEach(b => b.classList.remove('active'));
            if(btnElement) btnElement.classList.add('active');
            filterKits();
        }

        function filterKits() {
            const searchInput = document.getElementById('searchInput');
            const query = searchInput ? searchInput.value.toLowerCase() : '';
            
            const filtered = kits.filter(k => {
                const nameMatch = k.nombre ? k.nombre.toLowerCase().includes(query) : false;
                const descMatch = k.descripcion ? k.descripcion.toLowerCase().includes(query) : false;
                const creatorMatch = k.creador ? k.creador.toLowerCase().includes(query) : false;
                const idMatch = k.id ? k.id.includes(query) : false;

                const matchesSearch = nameMatch || descMatch || creatorMatch || idMatch;

                let matchesCat = true;
                if (selectedCategory === 'alta') matchesCat = k.altaDemanda === true;
                else if (selectedCategory === 'kit') matchesCat = k.categoria === 'kit';
                else if (selectedCategory === 'modelo') matchesCat = k.categoria === 'modelo';
                else if (selectedCategory === 'script') matchesCat = k.categoria === 'script';
                else if (selectedCategory === 'ui') matchesCat = k.categoria === 'ui';
                else if (selectedCategory === 'vip') matchesCat = k.isVip === true;

                return matchesSearch && matchesCat;
            });

            renderKits(filtered);
        }

        function toggleModal() {
            const pass = prompt("Introduce la contraseña de administrador:");
            if (pass === "70v26sfhF{wNAI<{(EHU") {
                const modal = document.getElementById('adminModal');
                if (modal) {
                    modal.style.display = modal.style.display === 'flex' ? 'none' : 'flex';
                }
            } else if (pass !== null) {
                alert("Contraseña incorrecta. Acceso denegado.");
            }
        }

        function addKit() {
            const img = document.getElementById('newImg').value;
            const name = document.getElementById('newName').value;
            const desc = document.getElementById('newDesc').value;
            const cat = document.getElementById('newCat').value;
            const author = document.getElementById('newAuthor').value || 'Desconocido';
            const id = document.getElementById('newId').value;
            const alta = document.getElementById('newAlta').value === 'true';

            if (!id || !name) {
                alert('Por favor ingresa al menos el ID y el Nombre del kit/modelo');
                return;
            }

            const newObj = {
                categoria: cat,
                altaDemanda: alta,
                creador: author,
                id: id,
                portada: img,
                nombre: name,
                descripcion: desc
            };

            kits.unshift(newObj);
            localStorage.setItem('studioDevs_items_v16', JSON.stringify(kits));
            filterKits();
            toggleModal();

            document.getElementById('newImg').value = '';
            document.getElementById('newName').value = '';
            document.getElementById('newDesc').value = '';
            document.getElementById('newAuthor').value = '';
            document.getElementById('newId').value = '';
        }

        function updateDemandStatusById() {
            const targetId = document.getElementById('targetId').value.trim();
            const newStatus = document.getElementById('targetStatus').value === 'true';

            if (!targetId) {
                alert('Por favor escribe el ID exacto de Roblox');
                return;
            }

            let found = false;
            kits.forEach(item => {
                if (item.id === targetId) {
                    item.altaDemanda = newStatus;
                    found = true;
                }
            });

            if (found) {
                localStorage.setItem('studioDevs_items_v16', JSON.stringify(kits));
                filterKits();
                toggleModal();
                alert('¡Estado de Alta Demanda actualizado con éxito!');
                document.getElementById('targetId').value = '';
            } else {
                alert('No se encontró ningún elemento con ese ID de Roblox.');
            }
        }

        window.onload = function() {
            renderKits(kits);
            document.getElementById('download-count').innerText = downloadCount.toLocaleString();
            
            setInterval(() => {
                const onlineEl = document.getElementById('online-count');
                if(onlineEl) {
                    let current = parseInt(onlineEl.innerText);
                    let change = Math.floor(Math.random() * 3) - 1;
                    let newVal = Math.max(2, current + change);
                    onlineEl.innerText = newVal;
                }
            }, 6000);
        };
    </script>
</head>
<body>

    <div class="header-container">
        <div class="header">
            <h1>Studio Devs</h1>
            <p>Modelos, Kits & Scripts Móviles</p>
            <div class="creator-info">Creador de esta página: htt_sii[span_0](start_span)[span_0](end_span)[span_1](start_span)[span_1](end_span)</div>
        </div>
        <button class="admin-btn" onclick="toggleModal()">⚙️</button>
    </div>

    <div class="stats-bar">
        <div class="stat-item">
            <span class="status-dot"></span>
            <span>En línea: <strong id="online-count">5</strong></span>
        </div>
        <div class="stat-item">
            <span>📥 Descargas: <strong id="download-count">1,248</strong></span>
        </div>
    </div>

    <div class="search-box">
        <span class="search-icon">🔍</span>
        <input type="text" id="searchInput" onkeyup="filterKits()" placeholder="Buscar modelos, kits o creadores...">
    </div>

    <div class="category-bar">
        <button class="cat-btn active" onclick="selectCategory('todos', this)">Todos</button>
        <button class="cat-btn" onclick="selectCategory('alta', this)">🔥 Alta Demanda</button>
        <button class="cat-btn" onclick="selectCategory('kit', this)">Kits</button>
        <button class="cat-btn" onclick="selectCategory('modelo', this)">Modelos</button>
        <button class="cat-btn" onclick="selectCategory('script', this)">Scripts</button>
        <button class="cat-btn" onclick="selectCategory('ui', this)">UI / Menús</button>
        <button class="cat-btn vip-tab" onclick="selectCategory('vip', this)">👑 Zona VIP</button>
    </div>

    <div class="section-title">🌐 Modelos Públicos</div>

    <div class="container" id="kitsContainer"></div>

    <div class="copyright-footer">
        © 2026 Studio Devs. Todos los derechos reservados.<br>
        Creador Oficial y Autoría: htt_sii[span_2](start_span)[span_2](end_span)[span_3](start_span)[span_3](end_span). Registrado bajo Copyright © Prohibida su copia o clonación no autorizada.
    </div>

    <!-- Modal de Administración -->
    <div class="modal" id="adminModal">
        <div class="modal-content">
            <div class="modal-header">
                <h3>Panel de Administración</h3>
                <button class="admin-btn" onclick="toggleModal()" style="position:static;">✕</button>
            </div>
            
            <!-- Sección 1: Publicar -->
            <h4 style="color:#00ff88; font-size:0.9rem; margin-bottom:8px;">Publicar Nuevo Contenido</h4>
            <div class="form-group">
                <label>1. URL de la Imagen de Portada</label>
                <input type="text" id="newImg" placeholder="https://i.ibb.co/...">
            </div>
            <div class="form-group">
                <label>2. Nombre del Kit o Modelo</label>
                <input type="text" id="newName" placeholder="Ej: Kit de Roba un Brainrot">
            </div>
            <div class="form-group">
                <label>3. Descripción (Debajo del nombre)</label>
                <textarea id="newDesc" rows="2" placeholder="Ej: Espero que lo disfrutes y te sea útil..."></textarea>
            </div>
            <div class="form-group">
                <label>4. Categoría</label>
                <select id="newCat">
                    <option value="kit">Kits</option>
                    <option value="modelo">Modelos</option>
                    <option value="script">Scripts</option>
                    <option value="ui">UI / Menú</option>
                </select>
            </div>
            <div class="form-group">
                <label>5. Creador y Plataforma</label>
                <input type="text" id="newAuthor" placeholder="Ej: Devfran (TikTok) o @RbxlProductInc (Roblox)">
            </div>
            <div class="form-group">
                <label>6. ID de Roblox</label>
                <input type="text" id="newId" placeholder="Ej: 95870844492917">
            </div>
            <div class="form-group">
                <label>¿Es de Alta Demanda? 🔥</label>
                <select id="newAlta">
                    <option value="false">Normal</option>
                    <option value="true">Sí (Alta Demanda)</option>
                </select>
            </div>
            <button class="btn-submit" onclick="addKit()">Publicar Contenido</button>

            <hr class="divider">

            <!-- Sección 2: Gestionar Alta Demanda por ID -->
            <h4 style="color:#fde047; font-size:0.9rem; margin-bottom:8px;">Gestionar Alta Demanda por ID 🔥</h4>
            <div class="form-group">
                <label>ID de Roblox del Modelo / Kit</label>
                <input type="text" id="targetId" placeholder="Ej: 95870844492917">
            </div>
            <div class="form-group">
                <label>Acción</label>
                <select id="targetStatus">
                    <option value="true">Poner en Alta Demanda 🔥</option>
                    <option value="false">Quitar de Alta Demanda</option>
                </select>
            </div>
            <button class="btn-submit" style="background:#fde047; color:#000;" onclick="updateDemandStatusById()">Actualizar Estado</button>
        </div>
    </div>
</body>
</html>
