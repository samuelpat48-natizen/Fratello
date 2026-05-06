<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>TiendaShop - Productos Premium</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            color: #333;
            line-height: 1.6;
        }

        /* Navbar */
        nav {
            background: rgba(255, 255, 255, 0.95);
            padding: 1rem 0;
            position: sticky;
            top: 0;
            box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
            z-index: 100;
            animation: slideDown 0.5s ease-out;
        }

        @keyframes slideDown {
            from {
                transform: translateY(-100%);
                opacity: 0;
            }
            to {
                transform: translateY(0);
                opacity: 1;
            }
        }

        .navbar-container {
            max-width: 1200px;
            margin: 0 auto;
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 0 2rem;
        }

        .logo {
            font-size: 1.8rem;
            font-weight: bold;
            background: linear-gradient(135deg, #667eea, #764ba2);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
        }

        .nav-links {
            display: flex;
            gap: 2rem;
            list-style: none;
        }

        .nav-links a {
            text-decoration: none;
            color: #333;
            font-weight: 500;
            position: relative;
            transition: color 0.3s ease;
            cursor: pointer;
        }

        .nav-links a::after {
            content: '';
            position: absolute;
            bottom: -5px;
            left: 0;
            width: 0;
            height: 2px;
            background: linear-gradient(135deg, #667eea, #764ba2);
            transition: width 0.3s ease;
        }

        .nav-links a:hover::after {
            width: 100%;
        }

        .nav-links a.active {
            color: #667eea;
        }

        .nav-links a.active::after {
            width: 100%;
        }

        /* Hero Section */
        .hero {
            max-width: 1200px;
            margin: 0 auto;
            padding: 4rem 2rem;
            text-align: center;
            color: white;
            animation: fadeIn 1s ease-out;
        }

        @keyframes fadeIn {
            from {
                opacity: 0;
                transform: translateY(20px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        .hero h1 {
            font-size: 3.5rem;
            margin-bottom: 1rem;
            animation: slideInDown 0.8s ease-out;
        }

        @keyframes slideInDown {
            from {
                transform: translateY(-50px);
                opacity: 0;
            }
            to {
                transform: translateY(0);
                opacity: 1;
            }
        }

        .hero p {
            font-size: 1.3rem;
            margin-bottom: 2rem;
            animation: slideInUp 0.8s ease-out 0.2s both;
        }

        @keyframes slideInUp {
            from {
                transform: translateY(50px);
                opacity: 0;
            }
            to {
                transform: translateY(0);
                opacity: 1;
            }
        }

        .btn {
            display: inline-block;
            padding: 0.8rem 2rem;
            margin: 0.5rem;
            border: none;
            border-radius: 50px;
            font-size: 1rem;
            font-weight: bold;
            cursor: pointer;
            transition: all 0.3s ease;
            animation: slideInUp 0.8s ease-out 0.4s both;
        }

        .btn-primary {
            background: white;
            color: #667eea;
        }

        .btn-primary:hover {
            transform: translateY(-3px);
            box-shadow: 0 10px 20px rgba(0, 0, 0, 0.2);
        }

        .btn-secondary {
            background: transparent;
            color: white;
            border: 2px solid white;
        }

        .btn-secondary:hover {
            background: white;
            color: #667eea;
            transform: translateY(-3px);
        }

        /* Main Content */
        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 0 2rem;
        }

        /* Section */
        .section {
            display: none;
            padding: 3rem 0;
            animation: fadeIn 0.6s ease-out;
        }

        .section.active {
            display: block;
        }

        /* Products Grid */
        .products {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
            gap: 2rem;
            margin: 2rem 0;
        }

        .product-card {
            background: white;
            border-radius: 15px;
            overflow: hidden;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.1);
            transition: all 0.3s ease;
            animation: scaleIn 0.6s ease-out;
        }

        @keyframes scaleIn {
            from {
                transform: scale(0.9);
                opacity: 0;
            }
            to {
                transform: scale(1);
                opacity: 1;
            }
        }

        .product-card:hover {
            transform: translateY(-10px);
            box-shadow: 0 15px 30px rgba(0, 0, 0, 0.2);
        }

        .product-image {
            width: 100%;
            height: 200px;
            background: linear-gradient(135deg, #667eea, #764ba2);
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 3rem;
            overflow: hidden;
        }

        .product-content {
            padding: 1.5rem;
        }

        .product-title {
            font-size: 1.3rem;
            margin-bottom: 0.5rem;
            color: #333;
        }

        .product-description {
            color: #666;
            font-size: 0.9rem;
            margin-bottom: 1rem;
        }

        .product-price {
            font-size: 1.5rem;
            font-weight: bold;
            color: #667eea;
            margin-bottom: 1rem;
        }

        .product-btn {
            width: 100%;
            padding: 0.8rem;
            background: linear-gradient(135deg, #667eea, #764ba2);
            color: white;
            border: none;
            border-radius: 8px;
            cursor: pointer;
            font-weight: bold;
            transition: all 0.3s ease;
        }

        .product-btn:hover {
            transform: scale(1.05);
            box-shadow: 0 5px 15px rgba(102, 126, 234, 0.4);
        }

        /* About Section */
        .about-content {
            background: white;
            padding: 2rem;
            border-radius: 15px;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.1);
            animation: fadeIn 0.6s ease-out;
        }

        .about-content h2 {
            color: #667eea;
            margin-bottom: 1rem;
        }

        .about-content p {
            color: #666;
            margin-bottom: 1rem;
        }

        /* Contact Section */
        .contact-form {
            background: white;
            padding: 2rem;
            border-radius: 15px;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.1);
            max-width: 600px;
            margin: 0 auto;
            animation: fadeIn 0.6s ease-out;
        }

        .form-group {
            margin-bottom: 1.5rem;
        }

        .form-group label {
            display: block;
            margin-bottom: 0.5rem;
            color: #333;
            font-weight: 500;
        }

        .form-group input,
        .form-group textarea {
            width: 100%;
            padding: 0.8rem;
            border: 2px solid #eee;
            border-radius: 8px;
            font-family: inherit;
            transition: border-color 0.3s ease;
        }

        .form-group input:focus,
        .form-group textarea:focus {
            outline: none;
            border-color: #667eea;
        }

        .form-group textarea {
            resize: vertical;
            min-height: 120px;
        }

        .form-submit {
            width: 100%;
            padding: 1rem;
            background: linear-gradient(135deg, #667eea, #764ba2);
            color: white;
            border: none;
            border-radius: 8px;
            font-weight: bold;
            cursor: pointer;
            transition: all 0.3s ease;
        }

        .form-submit:hover {
            transform: translateY(-3px);
            box-shadow: 0 10px 20px rgba(102, 126, 234, 0.4);
        }

        /* Footer */
        footer {
            background: rgba(0, 0, 0, 0.8);
            color: white;
            text-align: center;
            padding: 2rem;
            margin-top: 3rem;
        }

        /* Responsive */
        @media (max-width: 768px) {
            .hero h1 {
                font-size: 2rem;
            }

            .nav-links {
                gap: 1rem;
                font-size: 0.9rem;
            }

            .navbar-container {
                padding: 0 1rem;
            }
        }
    </style>
</head>
<body>
    <!-- Navigation -->
    <nav>
        <div class="navbar-container">
            <div class="logo">🛍️ TiendaShop</div>
            <ul class="nav-links">
                <li><a class="nav-link active" onclick="showSection('inicio')">Inicio</a></li>
                <li><a class="nav-link" onclick="showSection('productos')">Productos</a></li>
                <li><a class="nav-link" onclick="showSection('comprar')">Comprar</a></li>
                <li><a class="nav-link" onclick="showSection('about')">Nosotros</a></li>
                <li><a class="nav-link" onclick="showSection('contacto')">Contacto</a></li>
            </ul>
        </div>
    </nav>

    <!-- Hero Section -->
    <section class="section active" id="inicio">
        <div class="hero">
            <h1>Bienvenido a TiendaShop</h1>
            <p>Descubre productos de calidad con los mejores precios del mercado</p>
            <button class="btn btn-primary" onclick="showSection('productos')">Ver Productos</button>
            <button class="btn btn-secondary" onclick="showSection('comprar')">Ir a Comprar</button>
        </div>
    </section>

    <!-- Products Section -->
    <section class="section" id="productos">
        <div class="container">
            <h2 style="text-align: center; color: white; font-size: 2.5rem; margin-bottom: 2rem;">Nuestros Productos</h2>
            <div class="products">
                <div class="product-card">
                    <div class="product-image">📱</div>
                    <div class="product-content">
                        <h3 class="product-title">Smartphone Pro</h3>
                        <p class="product-description">Último modelo con tecnología avanzada</p>
                        <div class="product-price">$599.99</div>
                        <button class="product-btn" onclick="alert('Producto agregado al carrito')">Agregar al Carrito</button>
                    </div>
                </div>

                <div class="product-card">
                    <div class="product-image">⌚</div>
                    <div class="product-content">
                        <h3 class="product-title">Smartwatch Elite</h3>
                        <p class="product-description">Reloj inteligente con sensor de salud</p>
                        <div class="product-price">$299.99</div>
                        <button class="product-btn" onclick="alert('Producto agregado al carrito')">Agregar al Carrito</button>
                    </div>
                </div>

                <div class="product-card">
                    <div class="product-image">🎧</div>
                    <div class="product-content">
                        <h3 class="product-title">Auriculares Premium</h3>
                        <p class="product-description">Sonido de calidad estudio con cancelación de ruido</p>
                        <div class="product-price">$199.99</div>
                        <button class="product-btn" onclick="alert('Producto agregado al carrito')">Agregar al Carrito</button>
                    </div>
                </div>

                <div class="product-card">
                    <div class="product-image">💻</div>
                    <div class="product-content">
                        <h3 class="product-title">Laptop Gamer</h3>
                        <p class="product-description">Procesador de última generación para gaming</p>
                        <div class="product-price">$1,299.99</div>
                        <button class="product-btn" onclick="alert('Producto agregado al carrito')">Agregar al Carrito</button>
                    </div>
                </div>

                <div class="product-card">
                    <div class="product-image">📷</div>
                    <div class="product-content">
                        <h3 class="product-title">Cámara 4K</h3>
                        <p class="product-description">Captura videos en resolución ultra HD</p>
                        <div class="product-price">$899.99</div>
                        <button class="product-btn" onclick="alert('Producto agregado al carrito')">Agregar al Carrito</button>
                    </div>
                </div>

                <div class="product-card">
                    <div class="product-image">🎮</div>
                    <div class="product-content">
                        <h3 class="product-title">Consola Gaming</h3>
                        <p class="product-description">Consola de última generación con juegos incluidos</p>
                        <div class="product-price">$5680.00</div>
                        <button class="product-btn" onclick="alert('Producto agregado al carrito')">Agregar al Carrito</button>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- Shopping Section -->
    <section class="section" id="comprar">
        <div class="container">
            <h2 style="text-align: center; color: white; font-size: 2.5rem; margin-bottom: 2rem;">Realizar Compra</h2>
            <div style="background: white; padding: 2rem; border-radius: 15px;">
                <h3 style="margin-bottom: 1.5rem; color: #667eea;">Resumen de Compra</h3>
                <div style="background: #f8f9fa; padding: 1.5rem; border-radius: 8px; margin-bottom: 1.5rem;">
                    <p><strong>Subtotal:</strong> $0.00</p>
                    <p><strong>Impuestos:</strong> $0.00</p>
                    <p style="border-top: 2px solid #ddd; padding-top: 1rem; font-size: 1.2rem;"><strong>Total:</strong> $0.00</p>
                </div>
                <button class="btn btn-primary" style="width: 100%; margin-top: 1rem;" onclick="alert('¡Compra realizada exitosamente!')">Completar Compra</button>
                <button class="btn btn-secondary" style="width: 100%; margin-top: 0.5rem;" onclick="showSection('productos')">Seguir Comprando</button>
            </div>
        </div>
    </section>

    <!-- About Section -->
    <section class="section" id="about">
        <div class="container">
            <h2 style="text-align: center; color: white; font-size: 2.5rem; margin-bottom: 2rem;">Sobre Nosotros</h2>
            <div class="about-content">
                <h2>¿Quiénes Somos?</h2>
                <p>TiendaShop es una tienda online dedicada a ofrecer productos electrónicos de la más alta calidad. Contamos con más de 10 años de experiencia en el mercado y somos líderes en satisfacción del cliente.</p>
                <h2>Nuestra Misión</h2>
                <p>Proporcionar a nuestros clientes acceso a los mejores productos tecnológicos a precios competitivos, con un servicio al cliente excepcional.</p>
                <h2>¿Por Qué Elegirnos?</h2>
                <ul style="margin-left: 1.5rem; color: #666;">
                    <li>✓ Garantía de 2 años en todos nuestros productos</li>
                    <li>✓ Envío gratis en compras mayores a $50</li>
                    <li>✓ Servicio al cliente 24/7</li>
                    <li>✓ Política de devolución de 30 días</li>
                </ul>
            </div>
        </div>
    </section>

    <!-- Contact Section -->
    <section class="section" id="contacto">
        <div class="container">
            <h2 style="text-align: center; color: white; font-size: 2.5rem; margin-bottom: 2rem;">Contacto</h2>
            <form class="contact-form">
                <div class="form-group">
                    <label>Nombre</label>
                    <input type="text" placeholder="Tu nombre" required>
                </div>
                <div class="form-group">
                    <label>Email</label>
                    <input type="email" placeholder="Tu email" required>
                </div>
                <div class="form-group">
                    <label>Teléfono</label>
                    <input type="tel" placeholder="Tu teléfono">
                </div>
                <div class="form-group">
                    <label>Mensaje</label>
                    <textarea placeholder="Tu mensaje..." required></textarea>
                </div>
                <button type="submit" class="form-submit" onclick="event.preventDefault(); alert('¡Mensaje enviado exitosamente!')">Enviar Mensaje</button>
            </form>
        </div>
    </section>

    <!-- Footer -->
    <footer>
        <p>&copy; 2024 TiendaShop. Todos los derechos reservados.</p>
        <p>Email: info@tiendashop.com | Tel: +1-800-123-4567</p>
    </footer>

    <script>
        function showSection(sectionId) {
            // Hide all sections
            const sections = document.querySelectorAll('.section');
            sections.forEach(section => {
                section.classList.remove('active');
            });

            // Show selected section
            document.getElementById(sectionId).classList.add('active');

            // Update nav links
            const navLinks = document.querySelectorAll('.nav-link');
            navLinks.forEach(link => {
                link.classList.remove('active');
            });
            event.target.classList.add('active');

            // Scroll to top
            window.scrollTo(0, 0);
        }
    </script>
</body>
</html>
