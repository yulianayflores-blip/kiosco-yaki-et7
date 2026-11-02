[index.html](https://github.com/user-attachments/files/34275604/index.html)
<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Kiosco de Yaki - Escuela Técnica N°7</title>
    <!-- Tailwind CSS CDN -->
    <script src="https://cdn.tailwindcss.com"></script>
    <!-- FontAwesome Iconos -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <!-- Fuente Inter Google Fonts -->
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700;800&display=swap" rel="stylesheet">
    <style>
        body { font-family: 'Inter', sans-serif; }
    </style>
</head>
<body class="bg-zinc-100 text-zinc-800 min-h-screen flex flex-col">

    <!-- HEADER PRINCIPAL INSTITUCIONAL -->
    <header class="bg-zinc-900 text-white shadow-lg sticky top-0 z-50 border-b-4 border-emerald-500">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 py-4 flex flex-col sm:flex-row justify-between items-center gap-4">
            <div class="flex items-center space-x-3">
                <div class="bg-emerald-600 text-white p-3 rounded-2xl shadow-md flex items-center justify-center font-black text-2xl border border-emerald-400">
                    <i class="fa-solid fa-utensils"></i>
                </div>
                <div>
                    <h1 class="text-2xl sm:text-3xl font-extrabold tracking-tight text-white flex items-center gap-2">
                        Kiosco de Yaki
                    </h1>
                    <p class="text-xs sm:text-sm text-zinc-400 font-medium flex items-center gap-1">
                        <i class="fa-solid fa-graduation-cap text-emerald-400"></i> Escuela Técnica N°7
                    </p>
                </div>
            </div>

            <!-- Estado del Kiosco -->
            <div class="flex items-center gap-2 bg-zinc-800 text-emerald-400 text-xs px-3.5 py-2 rounded-xl border border-zinc-700 font-semibold">
                <span class="w-2.5 h-2.5 bg-emerald-500 rounded-full animate-pulse"></span> Abierto durante los recreos
            </div>
        </div>
    </header>

    <!-- CONTENIDO PRINCIPAL -->
    <main class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 py-8 flex-grow space-y-10 w-full">

        <!-- 1. PRIMER APARTADO: ENCONTRÁ ALFAJORES, GOLOSINAS, BEBIDAS Y SÁNDWICHES -->
        <section class="bg-white rounded-3xl p-6 sm:p-8 shadow-sm border border-zinc-200">
            <div class="flex flex-col md:flex-row md:items-center justify-between gap-4 mb-6">
                <div>
                    <h2 class="text-2xl font-black text-zinc-900 flex items-center gap-2">
                        <i class="fa-solid fa-cookie-bite text-emerald-600"></i> Encontrá alfajores, golosinas, bebidas y sándwiches
                    </h2>
                    <p class="text-xs sm:text-sm text-zinc-500">Seleccioná los productos y sumalos a tu cuenta del recreo</p>
                </div>

                <!-- Campo de Búsqueda -->
                <div class="relative w-full md:w-80">
                    <i class="fa-solid fa-search absolute left-3.5 top-1/2 -translate-y-1/2 text-zinc-400"></i>
                    <input type="text" id="searchInput" onkeyup="filterProducts()" placeholder="Buscar alfajor, bebida..." 
                        class="w-full pl-10 pr-4 py-2.5 bg-zinc-50 border border-zinc-300 rounded-xl text-sm focus:outline-none focus:ring-2 focus:ring-emerald-500 focus:bg-white transition-all">
                </div>
            </div>

            <!-- Botones de Filtro por Categorías -->
            <div class="flex flex-wrap gap-2 mb-6">
                <button onclick="filterCategory('todos')" class="cat-btn active border bg-emerald-600 text-white border-emerald-600 px-4 py-2 rounded-xl text-xs font-semibold shadow-sm transition-all">Todos</button>
                <button onclick="filterCategory('dulce')" class="cat-btn bg-zinc-100 text-zinc-700 hover:bg-zinc-200 border border-zinc-300 px-4 py-2 rounded-xl text-xs font-semibold transition-all">Cosas Dulces / Golosinas</button>
                <button onclick="filterCategory('bebida')" class="cat-btn bg-zinc-100 text-zinc-700 hover:bg-zinc-200 border border-zinc-300 px-4 py-2 rounded-xl text-xs font-semibold transition-all">Bebidas</button>
                <button onclick="filterCategory('salado')" class="cat-btn bg-zinc-100 text-zinc-700 hover:bg-zinc-200 border border-zinc-300 px-4 py-2 rounded-xl text-xs font-semibold transition-all">Salados / Sándwiches</button>
            </div>

            <!-- Grilla de Productos con Imágenes -->
            <div id="productList" class="grid grid-cols-1 sm:grid-cols-2 md:grid-cols-3 lg:grid-cols-4 gap-4">
                <!-- Se puebla dinámicamente desde JavaScript -->
            </div>
        </section>


        <!-- 2. SEGUNDO APARTADO: MENÚ PARA ALUMNOS -->
        <section class="bg-zinc-900 text-white rounded-3xl p-6 sm:p-8 shadow-xl border border-zinc-800 relative overflow-hidden">
            <div class="mb-6">
                <div class="inline-flex items-center gap-2 bg-emerald-600/20 text-emerald-400 px-3 py-1 rounded-full text-xs font-semibold border border-emerald-500/30 mb-2">
                    <i class="fa-solid fa-fire"></i> Lo más pedido en el patio
                </div>
                <h2 class="text-2xl sm:text-3xl font-black text-white">Menú para Alumnos</h2>
                <p class="text-xs sm:text-sm text-zinc-400">Platos preparados listos para retirar en el recreo</p>
            </div>

            <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-4 gap-4">
                <!-- Sánguche de Milanesa -->
                <div class="bg-zinc-800/90 rounded-2xl overflow-hidden border border-zinc-700 flex flex-col justify-between hover:border-emerald-500 transition-all">
                    <img src="https://images.unsplash.com/photo-1553909489-cd47e0907980?auto=format&fit=crop&w=400&q=80" alt="Milanesa" class="w-full h-32 object-cover" onerror="this.src='https://placehold.co/400x200/27272a/10b981?text=Sanguche+Milanesa'">
                    <div class="p-4 flex-grow flex flex-col justify-between">
                        <div>
                            <div class="flex justify-between items-center mb-1">
                                <h3 class="font-bold text-white text-base">Sánguche de Milanesa</h3>
                                <span class="bg-emerald-600 text-white text-xs px-2.5 py-1 rounded-lg font-bold">$3.500</span>
                            </div>
                            <p class="text-xs text-zinc-400">Carne o pollo en pan baguette con lechuga y tomate.</p>
                        </div>
                        <button onclick="addToCart('Sánguche de Milanesa', 3500)" class="mt-4 w-full bg-emerald-600 hover:bg-emerald-500 text-white text-xs font-bold py-2.5 rounded-xl transition-all flex items-center justify-center gap-2">
                            <i class="fa-solid fa-plus"></i> Agregar
                        </button>
                    </div>
                </div>

                <!-- Sánguche de Bondiola -->
                <div class="bg-zinc-800/90 rounded-2xl overflow-hidden border border-zinc-700 flex flex-col justify-between hover:border-emerald-500 transition-all">
                    <img src="https://images.unsplash.com/photo-1528735602780-2552fd46c7af?auto=format&fit=crop&w=400&q=80" alt="Bondiola" class="w-full h-32 object-cover" onerror="this.src='https://placehold.co/400x200/27272a/10b981?text=Sanguche+Bondiola'">
                    <div class="p-4 flex-grow flex flex-col justify-between">
                        <div>
                            <div class="flex justify-between items-center mb-1">
                                <h3 class="font-bold text-white text-base">Sánguche de Bondiola</h3>
                                <span class="bg-emerald-600 text-white text-xs px-2.5 py-1 rounded-lg font-bold">$4.000</span>
                            </div>
                            <p class="text-xs text-zinc-400">Bondiola tiernizada a la criolla.</p>
                        </div>
                        <button onclick="addToCart('Sánguche de Bondiola', 4000)" class="mt-4 w-full bg-emerald-600 hover:bg-emerald-500 text-white text-xs font-bold py-2.5 rounded-xl transition-all flex items-center justify-center gap-2">
                            <i class="fa-solid fa-plus"></i> Agregar
                        </button>
                    </div>
                </div>

                <!-- Panchos -->
                <div class="bg-zinc-800/90 rounded-2xl overflow-hidden border border-zinc-700 flex flex-col justify-between hover:border-emerald-500 transition-all">
                    <img src="https://images.unsplash.com/photo-1619740455993-9e612b1af08a?auto=format&fit=crop&w=400&q=80" alt="Pancho" class="w-full h-32 object-cover" onerror="this.src='https://placehold.co/400x200/27272a/10b981?text=Pancho+Completo'">
                    <div class="p-4 flex-grow flex flex-col justify-between">
                        <div>
                            <div class="flex justify-between items-center mb-1">
                                <h3 class="font-bold text-white text-base">Pancho Completo</h3>
                                <span class="bg-emerald-600 text-white text-xs px-2.5 py-1 rounded-lg font-bold">$1.500</span>
                            </div>
                            <p class="text-xs text-zinc-400">Con lluvia de papas y aderezos varios.</p>
                        </div>
                        <button onclick="addToCart('Pancho Completo', 1500)" class="mt-4 w-full bg-emerald-600 hover:bg-emerald-500 text-white text-xs font-bold py-2.5 rounded-xl transition-all flex items-center justify-center gap-2">
                            <i class="fa-solid fa-plus"></i> Agregar
                        </button>
                    </div>
                </div>

                <!-- Pizzetas -->
                <div class="bg-zinc-800/90 rounded-2xl overflow-hidden border border-zinc-700 flex flex-col justify-between hover:border-emerald-500 transition-all">
                    <img src="https://images.unsplash.com/photo-1513104890138-7c749659a591?auto=format&fit=crop&w=400&q=80" alt="Pizzeta" class="w-full h-32 object-cover" onerror="this.src='https://placehold.co/400x200/27272a/10b981?text=Pizzeta+Muzzarella'">
                    <div class="p-4 flex-grow flex flex-col justify-between">
                        <div>
                            <div class="flex justify-between items-center mb-1">
                                <h3 class="font-bold text-white text-base">Pizzeta Muzzarella</h3>
                                <span class="bg-emerald-600 text-white text-xs px-2.5 py-1 rounded-lg font-bold">$1.800</span>
                            </div>
                            <p class="text-xs text-zinc-400">Salsa de tomate casera y abundante queso.</p>
                        </div>
                        <button onclick="addToCart('Pizzeta Muzzarella', 1800)" class="mt-4 w-full bg-emerald-600 hover:bg-emerald-500 text-white text-xs font-bold py-2.5 rounded-xl transition-all flex items-center justify-center gap-2">
                            <i class="fa-solid fa-plus"></i> Agregar
                        </button>
                    </div>
                </div>
            </div>
        </section>


        <!-- 3. TERCER APARTADO: MENÚ PARA PROFESORES -->
        <section class="bg-zinc-800 text-white rounded-3xl p-6 sm:p-8 shadow-md border border-zinc-700 relative overflow-hidden">
            <div class="flex flex-col md:flex-row md:items-center justify-between gap-4 mb-6">
                <div>
                    <div class="inline-flex items-center gap-2 bg-emerald-500/20 text-emerald-300 px-3 py-1 rounded-full text-xs font-semibold border border-emerald-500/30 mb-2">
                        <i class="fa-solid fa-user-tie"></i> Exclusivo Docentes
                    </div>
                    <h2 class="text-2xl sm:text-3xl font-black text-white">Menú para Profesores</h2>
                    <p class="text-xs sm:text-sm text-zinc-300">Comida casera caliente enviada directamente a la sala de profesores</p>
                </div>

                <!-- Cartel de Horario para Profesores -->
                <div class="bg-zinc-900 border border-emerald-500/50 rounded-2xl p-3.5 flex items-center gap-3">
                    <i class="fa-solid fa-clock text-emerald-400 text-xl"></i>
                    <div>
                        <p class="text-xs text-zinc-400 font-semibold uppercase tracking-wider">Horario de Pedidos</p>
                        <p class="text-xs sm:text-sm font-bold text-white">Se empieza a pedir a partir de las <span class="text-emerald-400 font-extrabold">12:30 PM</span></p>
                    </div>
                </div>
            </div>

            <!-- Grilla de Menú de Profes -->
            <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-4 gap-4">
                <!-- Ñoquis -->
                <div class="bg-zinc-900/80 rounded-2xl overflow-hidden border border-zinc-700/80 hover:border-emerald-500 transition-all flex flex-col justify-between">
                    <img src="https://images.unsplash.com/photo-1551183053-bf91a1d81141?auto=format&fit=crop&w=400&q=80" alt="Ñoquis" class="w-full h-32 object-cover" onerror="this.src='https://placehold.co/400x200/18181b/10b981?text=Noquis+Caseros'">
                    <div class="p-4 flex-grow flex flex-col justify-between">
                        <div>
                            <div class="flex justify-between items-center mb-1">
                                <h3 class="font-bold text-white text-base">Ñoquis Caseros</h3>
                                <span class="bg-emerald-600 text-white text-xs px-2.5 py-1 rounded-lg font-bold">$4.500</span>
                            </div>
                            <p class="text-xs text-zinc-400">Con salsa tuco y queso rallado.</p>
                        </div>
                        <button onclick="addToCart('Ñoquis Caseros (Profes)', 4500)" class="mt-4 w-full bg-emerald-600 hover:bg-emerald-500 text-white text-xs font-bold py-2.5 rounded-xl transition-all flex items-center justify-center gap-2">
                            <i class="fa-solid fa-plus"></i> Agregar
                        </button>
                    </div>
                </div>

                <!-- Pollo con Papas -->
                <div class="bg-zinc-900/80 rounded-2xl overflow-hidden border border-zinc-700/80 hover:border-emerald-500 transition-all flex flex-col justify-between">
                    <img src="https://images.unsplash.com/photo-1598515214211-89d3c73ae83b?auto=format&fit=crop&w=400&q=80" alt="Pollo" class="w-full h-32 object-cover" onerror="this.src='https://placehold.co/400x200/18181b/10b981?text=Pollo+con+Papas'">
                    <div class="p-4 flex-grow flex flex-col justify-between">
                        <div>
                            <div class="flex justify-between items-center mb-1">
                                <h3 class="font-bold text-white text-base">Pollo con Papas</h3>
                                <span class="bg-emerald-600 text-white text-xs px-2.5 py-1 rounded-lg font-bold">$5.200</span>
                            </div>
                            <p class="text-xs text-zinc-400">Patamuslo al horno con papas rústicas.</p>
                        </div>
                        <button onclick="addToCart('Pollo con Papas (Profes)', 5200)" class="mt-4 w-full bg-emerald-600 hover:bg-emerald-500 text-white text-xs font-bold py-2.5 rounded-xl transition-all flex items-center justify-center gap-2">
                            <i class="fa-solid fa-plus"></i> Agregar
                        </button>
                    </div>
                </div>

                <!-- Ensalada Completa -->
                <div class="bg-zinc-900/80 rounded-2xl overflow-hidden border border-zinc-700/80 hover:border-emerald-500 transition-all flex flex-col justify-between">
                    <img src="https://images.unsplash.com/photo-1512621776951-a57141f2eefd?auto=format&fit=crop&w=400&q=80" alt="Ensalada" class="w-full h-32 object-cover" onerror="this.src='https://placehold.co/400x200/18181b/10b981?text=Ensalada+Completa'">
                    <div class="p-4 flex-grow flex flex-col justify-between">
                        <div>
                            <div class="flex justify-between items-center mb-1">
                                <h3 class="font-bold text-white text-base">Ensalada Completa</h3>
                                <span class="bg-emerald-600 text-white text-xs px-2.5 py-1 rounded-lg font-bold">$3.800</span>
                            </div>
                            <p class="text-xs text-zinc-400">Lechuga, tomate, huevo, choclo y pollo opcional.</p>
                        </div>
                        <button onclick="addToCart('Ensalada Completa (Profes)', 3800)" class="mt-4 w-full bg-emerald-600 hover:bg-emerald-500 text-white text-xs font-bold py-2.5 rounded-xl transition-all flex items-center justify-center gap-2">
                            <i class="fa-solid fa-plus"></i> Agregar
                        </button>
                    </div>
                </div>

                <!-- Combo Docente -->
                <div class="bg-zinc-900/80 rounded-2xl overflow-hidden border border-zinc-700/80 hover:border-emerald-500 transition-all flex flex-col justify-between">
                    <img src="https://images.unsplash.com/photo-1546069901-ba9599a7e63c?auto=format&fit=crop&w=400&q=80" alt="Combo" class="w-full h-32 object-cover" onerror="this.src='https://placehold.co/400x200/18181b/10b981?text=Combo+Docente'">
                    <div class="p-4 flex-grow flex flex-col justify-between">
                        <div>
                            <div class="flex justify-between items-center mb-1">
                                <h3 class="font-bold text-white text-base">Combo Docente</h3>
                                <span class="bg-emerald-600 text-white text-xs px-2.5 py-1 rounded-lg font-bold">$6.500</span>
                            </div>
                            <p class="text-xs text-zinc-400">Plato principal + Bebida 500ml + Fruta / Postre.</p>
                        </div>
                        <button onclick="addToCart('Combo Docente (Profes)', 6500)" class="mt-4 w-full bg-emerald-600 hover:bg-emerald-500 text-white text-xs font-bold py-2.5 rounded-xl transition-all flex items-center justify-center gap-2">
                            <i class="fa-solid fa-plus"></i> Agregar
                        </button>
                    </div>
                </div>
            </div>
        </section>


        <!-- 4. CUARTO APARTADO: CALCULADORA, TOTAL Y ENVÍO DEL PEDIDO A YAKI POR WHATSAPP -->
        <section id="calculadora" class="bg-white rounded-3xl p-6 sm:p-8 shadow-md border border-zinc-200">
            <div class="flex items-center justify-between border-b border-zinc-200 pb-4 mb-6">
                <div>
                    <h2 class="text-2xl font-black text-zinc-900 flex items-center gap-2">
                        <i class="fa-solid fa-calculator text-emerald-600"></i> Tu Cuenta del Recreo
                    </h2>
                    <p class="text-xs sm:text-sm text-zinc-500">Revisá tu pedido, calculá el total y mandáselo a Yaki</p>
                </div>
                <button onclick="clearCart()" class="text-xs text-red-500 hover:text-red-700 font-bold flex items-center gap-1 transition-all">
                    <i class="fa-solid fa-trash"></i> Vaciar
                </button>
            </div>

            <!-- Lista de items agregados -->
            <div id="cartItems" class="space-y-3 mb-6 max-h-60 overflow-y-auto pr-2">
                <p id="emptyCartText" class="text-center text-zinc-400 text-sm py-8">
                    No agregaste ningún producto a la cuenta todavía.
                </p>
            </div>

            <!-- Datos del Cliente para enviar a Yaki -->
            <div class="grid grid-cols-1 sm:grid-cols-2 gap-4 mb-6 bg-zinc-50 p-4 rounded-2xl border border-zinc-200">
                <div>
                    <label class="block text-xs font-bold text-zinc-700 mb-1">Tu Nombre:</label>
                    <input type="text" id="clientName" placeholder="Ej: Lucas o Profe Gómez" class="w-full px-3 py-2 bg-white border border-zinc-300 rounded-xl text-xs focus:ring-2 focus:ring-emerald-500 focus:outline-none">
                </div>
                <div>
                    <label class="block text-xs font-bold text-zinc-700 mb-1">Curso o Sala:</label>
                    <input type="text" id="clientCourse" placeholder="Ej: 6° 2° Computación / Sala Profes" class="w-full px-3 py-2 bg-white border border-zinc-300 rounded-xl text-xs focus:ring-2 focus:ring-emerald-500 focus:outline-none">
                </div>
            </div>

            <!-- Total Final y Botón WhatsApp para Yaki -->
            <div class="bg-zinc-900 text-white p-5 rounded-2xl flex flex-col md:flex-row justify-between items-center gap-4">
                <div>
                    <span class="text-xs text-zinc-400 uppercase tracking-wider font-semibold">Total a Pagar</span>
                    <h3 id="cartTotal" class="text-3xl font-black text-emerald-400">$0</h3>
                </div>

                <button onclick="sendOrderToYaki()" class="w-full md:w-auto bg-emerald-600 hover:bg-emerald-500 text-white font-extrabold px-6 py-3.5 rounded-xl shadow-lg transition-all flex items-center justify-center gap-2 text-sm">
                    <i class="fa-brands fa-whatsapp text-lg"></i> Enviar Pedido a Yaki
                </button>
            </div>
        </section>

    </main>

    <!-- FOOTER INSTITUCIONAL -->
    <footer class="bg-zinc-900 text-zinc-400 py-6 border-t border-zinc-800 text-center text-xs mt-auto">
        <div class="max-w-7xl mx-auto px-4">
            <p class="font-semibold text-zinc-300 mb-1">Proyecto Final - Escuela Técnica N°7</p>
            <p>Desarrollado para el Kiosco de Yaki &copy; 2026</p>
        </div>
    </footer>

    <!-- LÓGICA JAVASCRIPT -->
    <script>
        // Lista de productos del kiosco
        const products = [
            { name: "Alfajor Guaymallén", price: 600, cat: "dulce", img: "https://images.unsplash.com/photo-1590080875515-8a3a8dc5735e?auto=format&fit=crop&w=300&q=80" },
            { name: "Alfajor Capitán del Espacio", price: 1000, cat: "dulce", img: "https://images.unsplash.com/photo-1558961363-fa8fdf82db35?auto=format&fit=crop&w=300&q=80" },
            { name: "Gaseosa 500ml", price: 1500, cat: "bebida", img: "https://images.unsplash.com/photo-1622483767028-3f66f32aef97?auto=format&fit=crop&w=300&q=80" },
            { name: "Agua Mineral / Saborizada", price: 1200, cat: "bebida", img: "https://images.unsplash.com/photo-1548839140-29a749e1bc4e?auto=format&fit=crop&w=300&q=80" },
            { name: "Papas Fritas / Snacks", price: 1100, cat: "salado", img: "https://images.unsplash.com/photo-1566478989037-eec170784d0b?auto=format&fit=crop&w=300&q=80" },
            { name: "Empanadas de Carne/J&Q", price: 1200, cat: "salado", img: "https://images.unsplash.com/photo-1626700051175-6818013e1d4f?auto=format&fit=crop&w=300&q=80" },
            { name: "Caramelos y Golosinas", price: 300, cat: "dulce", img: "https://images.unsplash.com/photo-1582058091505-f87a2e55a40f?auto=format&fit=crop&w=300&q=80" },
            { name: "Jugo en Cajita / Sobre", price: 500, cat: "bebida", img: "https://images.unsplash.com/photo-1613478223719-2ab802602423?auto=format&fit=crop&w=300&q=80" }
        ];

        // Estado del Carrito / Calculadora
        let cart = [];

        // Renderizado de productos
        function renderProducts(items) {
            const container = document.getElementById('productList');
            container.innerHTML = '';
            
            items.forEach(prod => {
                const card = document.createElement('div');
                card.className = "bg-zinc-50 border border-zinc-200 rounded-2xl overflow-hidden flex flex-col justify-between hover:border-emerald-500 hover:shadow-md transition-all";
                card.innerHTML = `
                    <img src="${prod.img}" alt="${prod.name}" class="w-full h-28 object-cover" onerror="this.src='https://placehold.co/300x150/f4f4f5/10b981?text=Producto'">
                    <div class="p-3.5 flex-grow flex flex-col justify-between">
                        <div>
                            <div class="flex justify-between items-start mb-1">
                                <h4 class="font-bold text-zinc-800 text-sm">${prod.name}</h4>
                            </div>
                            <span class="inline-block bg-zinc-200 text-zinc-900 text-xs px-2 py-0.5 rounded-md font-extrabold mb-2">$${prod.price}</span>
                        </div>
                        <button onclick="addToCart('${prod.name}', ${prod.price})" class="mt-2 w-full bg-zinc-900 hover:bg-emerald-600 text-white text-xs font-bold py-2 rounded-xl transition-all flex items-center justify-center gap-1">
                            <i class="fa-solid fa-plus text-emerald-400"></i> Agregar
                        </button>
                    </div>
                `;
                container.appendChild(card);
            });
        }

        // Filtrar por búsqueda
        function filterProducts() {
            const query = document.getElementById('searchInput').value.toLowerCase();
            const filtered = products.filter(p => p.name.toLowerCase().includes(query));
            renderProducts(filtered);
        }

        // Filtrar por categoría
        function filterCategory(cat) {
            document.querySelectorAll('.cat-btn').forEach(btn => {
                btn.className = "cat-btn bg-zinc-100 text-zinc-700 hover:bg-zinc-200 border border-zinc-300 px-4 py-2 rounded-xl text-xs font-semibold transition-all";
            });
            event.target.className = "cat-btn active bg-emerald-600 text-white border border-emerald-600 px-4 py-2 rounded-xl text-xs font-semibold shadow-sm transition-all";

            if (cat === 'todos') {
                renderProducts(products);
            } else {
                const filtered = products.filter(p => p.cat === cat);
                renderProducts(filtered);
            }
        }

        // Agregar al carrito
        function addToCart(name, price) {
            const existing = cart.find(item => item.name === name);
            if (existing) {
                existing.qty++;
            } else {
                cart.push({ name, price, qty: 1 });
            }
            updateCartUI();
        }

        // Cambiar cantidad
        function changeQty(name, delta) {
            const item = cart.find(i => i.name === name);
            if (item) {
                item.qty += delta;
                if (item.qty <= 0) {
                    cart = cart.filter(i => i.name !== name);
                }
            }
            updateCartUI();
        }

        // Vaciar carrito
        function clearCart() {
            cart = [];
            updateCartUI();
        }

        // Actualizar interfaz del carrito
        function updateCartUI() {
            const container = document.getElementById('cartItems');
            const totalEl = document.getElementById('cartTotal');
            
            if (cart.length === 0) {
                container.innerHTML = `<p id="emptyCartText" class="text-center text-zinc-400 text-sm py-8">No agregaste ningún producto a la cuenta todavía.</p>`;
                totalEl.innerText = '$0';
                return;
            }

            container.innerHTML = '';
            let total = 0;

            cart.forEach(item => {
                const subtotal = item.price * item.qty;
                total += subtotal;

                const div = document.createElement('div');
                div.className = "flex justify-between items-center bg-zinc-50 p-3 rounded-xl border border-zinc-200 text-sm";
                div.innerHTML = `
                    <div class="flex-grow">
                        <p class="font-bold text-zinc-800">${item.name}</p>
                        <p class="text-xs text-zinc-500">$${item.price} c/u</p>
                    </div>
                    <div class="flex items-center gap-3">
                        <div class="flex items-center border border-zinc-300 rounded-lg overflow-hidden bg-white">
                            <button onclick="changeQty('${item.name}', -1)" class="px-2 py-1 text-zinc-600 hover:bg-zinc-100 font-bold">-</button>
                            <span class="px-2 text-xs font-bold text-zinc-800">${item.qty}</span>
                            <button onclick="changeQty('${item.name}', 1)" class="px-2 py-1 text-zinc-600 hover:bg-zinc-100 font-bold">+</button>
                        </div>
                        <span class="font-bold text-zinc-900 text-sm w-20 text-right">$${subtotal}</span>
                    </div>
                `;
                container.appendChild(div);
            });

            totalEl.innerText = `$${total.toLocaleString('es-AR')}`;
        }

        // Enviar pedido a Yaki por WhatsApp (+54 9 266 457 0170)
        function sendOrderToYaki() {
            if (cart.length === 0) {
                alert("Agregá al menos un producto a la cuenta antes de enviar el pedido.");
                return;
            }

            const name = document.getElementById('clientName').value.trim() || "Alumno/a";
            const course = document.getElementById('clientCourse').value.trim() || "Escuela Técnica N°7";

            let message = `*NUEVO PEDIDO - KIOSCO DE YAKI (ET N°7)*\n`;
            message += `👤 *De:* ${name}\n`;
            message += `🏫 *Curso/Rol:* ${course}\n\n`;
            message += `*Detalle del pedido:*\n`;

            let total = 0;
            cart.forEach(item => {
                const subtotal = item.price * item.qty;
                total += subtotal;
                message += `• ${item.qty}x ${item.name} - $${subtotal}\n`;
            });

            message += `\n💰 *TOTAL A PAGAR:* $${total.toLocaleString('es-AR')}`;

            const encodedMessage = encodeURIComponent(message);
            const whatsappUrl = `https://wa.me/5492664570170?text=${encodedMessage}`;
            
            window.open(whatsappUrl, '_blank');
        }

        // Cargar productos al inicio
        window.onload = function() {
            renderProducts(products);
        };
    </script>
</body>
</html>
