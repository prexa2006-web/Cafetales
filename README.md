# Cafetales
# ☕ CafeTales — Premium Café Management System

CafeTales is a modern, responsive full-stack web application designed for a premium coffee shop experience. It features a fully responsive customer-facing website with dynamic sliders, instant food menu configurations, an asynchronous shopping cart, physical table seating maps, dynamic slot-availability validation, and a secured administrative control dashboard.

---

## 🚀 Key Features

### 👤 Customer-Facing Portal
* **Video-Style Hero Slider:** A modular left-aligned text layer with dynamic multi-layer slide transitions synced with auto-pausing queue thumbs logic.
* **Instant Dynamic Menu Grid:** Filterable menu items synced via category mapping fetched dynamically from database schemas with state-safe async optimistic rendering logic.
* **Asynchronous Cart Flow:** Instant persistent item counter integrations with interactive totals calculation on a dedicated floating bottom control panel layout.
* **Smart Table Assignment & Real-Time Availability:** Dynamic capacity lookup checks available slots (max 10 per area) for 'Indoor', 'Outdoor', or 'Window' sections on a specific date/time. Valid allocations trigger a random unique table assignment to prevent double bookings.
* **Personalized Dashboard & Order History (`my_bookings.html`):** Registered customers can view a unified history of their past table bookings (with live status states like Confirmed/Pending) and precise order receipts showing concatenated lists of items purchased (`Item x Quantity`).
* **Visual Triggers & Special Promotions:** Interactive reveal mechanics powered by scroll observers and custom promotion layouts showcasing running offers.

### 🛡️ Admin Dashboard Features
* **Stat Tracking Overview:** Automated overview boxes pulling real-time performance insights for Pending Bookings count, Active Menu Items count, and Gross Aggregated Revenue (₹).
* **Live Orders Monitor:** Colored state boundaries mapping incoming orders per table alongside structural payment tracking switches (`Paid` / `Unpaid`).
* **Dynamic Content Management System:** Native item insert templates with dynamic upload mechanics streaming parameters directly inside dedicated upload storage directories.
* **Live Reservation Controller:** Dynamic interface buttons giving structural administrators absolute authorization states to toggle customer booking properties between `Confirmed`, `Pending`, or `Cancelled`.

---

## 🛠️ Tech Stack & Architecture

### Frontend
* **Core Layout Engines:** HTML5 Semantic Markup & Customized Vanilla CSS Variables Layer.
* **Responsive Layout Library:** Bootstrap 5.3.3 Interface Layer.
* **Client State Controller:** Pure Native Vanilla JavaScript (ES6+ Standards) utilizing explicit custom class paradigms, asynchronous fetch API calls, crypto mapping entities, and FormData objects.

### Backend & Database Layer
* **Server Implementation:** Procedural PHP 8+ Script Engines with integrated Access-Control-Allow structural boundaries.
* **Data Persistence Engine:** Structured Relational MySQL Database Engine utilizing fully prepared statement bindings to strongly counter structural query injection payloads.
* **Session Handler Pattern:** Hybrid Role-Validation architecture linking LocalStorage state variables (`cafetales_session_v3`) to back-end permission verification arrays.

---

## 📁 Repository Structure Mapping

```text
├── about.html          # Public profile page with historical brand timeline maps
├── admin.html          # Administrative revenue monitor and reservation controller
├── api.php             # Core back-end business processor handling checkout, slots, & seating
├── auth.js             # Client interface script bridging sign-up form triggers
├── auth_api.php        # Credential handling subsystem with plain comparison checks
├── cart.html           # Layout reviewing chosen selections with automated QR generators
├── contact.html        # Message validation UI with local iframe embed properties
├── contact_api.php     # Multi-method endpoint sorting incoming visitor inquiries
├── db_connect.php      # Base structural database connection initialization handle
├── events.html         # Local workshop register system with custom tick timers
├── gallery.html        # Aesthetic photo grid mapping local ambiance elements
├── global.css          # Central variable architecture and component reset rules
├── global.js           # Injection scripts generating contextual avatar structures & dynamic cart badges
├── hero-slider.js      # Foreground carousel state array layout switcher rules
├── index.html          # Root portal loading entry parameters and featured assets
├── login.html          # Interactive dual-view authentication entry template
├── menu.html           # Product overview grid with persistent floating counters
├── my_bookings.html    # Customer panel displaying personal real-time booking and checkout history
├── offers.html         # Promotions page rendering active discounts and coupon codes
├── README.md           # Master system documentation file
├── reservation.html    # Front-end table reservation layout with live slot validation feeds
└── reservation.js      # Form validation and dynamic availability script querying the core API
💻 Installation & Configuration
📋 Prerequisites
Install a local server management environment such as XAMPP, WampServer, or MAMP.

Ensure Apache Server and MySQL Server modules are active.

⚙️ Setting Up Local Database Environment
Open your browser and navigate to your database manager: http://localhost/phpmyadmin/.

Create an empty database instance exactly named cafetales.

Import the database layout structure schema (via your structural migration .sql file or use the schema outline below).
CREATE TABLE IF NOT EXISTS `users` (
  `id` INT AUTO_INCREMENT PRIMARY KEY,
  `full_name` VARCHAR(100),
  `email` VARCHAR(100) UNIQUE,
  `password_hash` VARCHAR(255),
  `role` ENUM('customer', 'admin') DEFAULT 'customer'
);

CREATE TABLE IF NOT EXISTS `categories` (
  `id` INT AUTO_INCREMENT PRIMARY KEY,
  `name` VARCHAR(50)
);

CREATE TABLE IF NOT EXISTS `menu_items` (
  `id` INT AUTO_INCREMENT PRIMARY KEY,
  `name` VARCHAR(100),
  `price` DECIMAL(10,2),
  `category_id` INT,
  `image` VARCHAR(255) DEFAULT 'default.jpg',
  `is_available` TINYINT(1) DEFAULT 1,
  FOREIGN KEY (`category_id`) REFERENCES `categories`(`id`)
);

CREATE TABLE IF NOT EXISTS `reservations` (
  `id` INT AUTO_INCREMENT PRIMARY KEY,
  `user_id` INT,
  `customer_name` VARCHAR(100),
  `customer_phone` VARCHAR(20),
  `reservation_date` DATE,
  `reservation_time` TIME,
  `guests` INT,
  `seating_area` VARCHAR(50),
  `table_number` INT,
  `notes` TEXT,
  `status` ENUM('pending', 'confirmed', 'cancelled') DEFAULT 'pending'
);

CREATE TABLE IF NOT EXISTS `orders` (
  `id` INT AUTO_INCREMENT PRIMARY KEY,
  `user_id` INT,
  `total_amount` DECIMAL(10,2),
  `status` VARCHAR(20) DEFAULT 'pending',
  `table_number` VARCHAR(20),
  `payment_method` VARCHAR(50),
  `payment_status` VARCHAR(20) DEFAULT 'Pending',
  `order_date` TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

CREATE TABLE IF NOT EXISTS `messages` (
  `id` INT AUTO_INCREMENT PRIMARY KEY,
  `name` VARCHAR(100),
  `email` VARCHAR(100),
  `phone` VARCHAR(20),
  `message` TEXT,
  `sent_at` TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
🏃 Setting Up Local Subsystem Deployment
Move the complete project directory inside your local runtime web-accessible location (e.g., C:/xampp/htdocs/Cafetales/).

Verify structural configuration targets inside your initialization scripts (db_connect.php & contact_api.php) map valid parameter fields:

PHP
$conn = new mysqli("localhost", "root", "", "cafetales");
Open your favorite web browser interface and type the local deployment address string to initialize code tracking:

Plaintext
http://localhost/Cafetales/index.html