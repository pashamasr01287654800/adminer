# Adminer - Database Management Tool 📊

[![Adminer Version](https://img.shields.io/badge/Adminer-4.8.1-blue.svg)](https://www.adminer.org)
[![PHP Version](https://img.shields.io/badge/PHP-7.4%2B-purple.svg)](https://php.net)
[![License](https://img.shields.io/badge/License-Apache%202.0-green.svg)](https://opensource.org/licenses/Apache-2.0)
[![Downloads](https://img.shields.io/github/downloads/yourusername/adminer/total)]()
[![GitHub Stars](https://img.shields.io/github/stars/yourusername/adminer)]()

## 📋 Overview

Adminer.php is a full-featured database management tool in a single PHP file. It serves as a lightweight, more secure alternative to phpMyAdmin, supporting multiple database systems through a clean and intuitive interface.

## ✨ Features

### Core Features
- **Single File** - No complex installation required, just upload and use
- **Lightweight** - File size less than 500KB
- **High Security** - Built-in protection against SQL injection attacks
- **Responsive Design** - Works perfectly on desktop, tablet, and mobile

### Database Support
| Database | Support | Version |
|----------|---------|---------|
| MySQL / MariaDB | ✅ Full | 5.5+ |
| PostgreSQL | ✅ Full | 9.0+ |
| SQLite | ✅ Full | 3.x |
| MS SQL | ✅ Full | 2008+ |
| Oracle | ✅ Full | 10g+ |
| Firebird | ✅ Full | 2.5+ |
| SimpleDB | ✅ Basic | - |
| Elasticsearch | ✅ Basic | 5.x+ |
| MongoDB | ⚠️ Plugin | - |

### Data Management
- **Create, modify, delete** databases and tables
- **User & privilege management**
- **Execute SQL queries** with syntax highlighting
- **Import/Export** data in multiple formats (SQL, CSV, JSON, XML)
- **Search and filter** capabilities
- **View table structures** and relationships
- **Index management**
- **Trigger, view, and procedure** support
- **Foreign key management**
- **Full-text search support**

## 🚀 Quick Installation

### Method 1: Direct Upload (Simplest)
```bash
# Download the latest version
wget https://www.adminer.org/latest-en.php -O adminer.php

# Or using curl
curl -o adminer.php https://www.adminer.org/latest-en.php

# Download with custom name for security
wget https://www.adminer.org/latest-en.php -O db-manager.php
```

Then upload the file to your server and access it via browser.

Method 2: Using Docker

```bash
# Run Adminer container
docker run -d -p 8080:8080 --name adminer adminer

# Or with specific database server
docker run -d -p 8080:8080 --name adminer \
  -e ADMINER_DEFAULT_SERVER=mysql-server \
  adminer

# With custom theme
docker run -d -p 8080:8080 --name adminer \
  -e ADMINER_DESIGN=pepa-linha \
  adminer
```

Access at: http://localhost:8080

Method 3: Local Development (XAMPP/WAMP/MAMP)

1. Download adminer.php
2. Copy to:
   · XAMPP: C:\xampp\htdocs\
   · WAMP: C:\wamp64\www\
   · MAMP: /Applications/MAMP/htdocs/
   · Linux: /var/www/html/
3. Start your local server
4. Open: http://localhost/adminer.php

Method 4: Using Composer

```bash
composer require adminer/adminer

# Or for specific version
composer require adminer/adminer:4.8.1
```

Method 5: Using Package Managers

```bash
# Ubuntu/Debian
sudo apt-get install adminer

# MacOS with Homebrew
brew install adminer

# FreeBSD
pkg install adminer
```

🔧 Usage Guide

Login Credentials

When you first open Adminer, you'll need to provide:

```
System:     [MySQL, PostgreSQL, SQLite, ...]
Server:     [localhost or IP address:port]
Username:   [your database username]
Password:   [your database password]
Database:   [optional - specific database name]
```

Common Operations

Managing Databases

```sql
-- Create new database
CREATE DATABASE database_name CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci;

-- Drop database (be careful!)
DROP DATABASE database_name;

-- Backup database
-- Use export feature to download SQL dump
```

Working with Tables

· Create Table: Click "Create table" → Define columns → Save
· Modify Table: Select table → Click "Alter table"
· Browse Data: Click table name → Use filters and sorting
· Search: Advanced search with multiple conditions
· Export: Choose format and options

SQL Query Execution

1. Click "SQL command" in the sidebar
2. Write or paste your query
3. Use keyboard shortcut (Ctrl+Enter or Cmd+Enter) to execute
4. View and export results

Keyboard Shortcuts

Shortcut Action
Ctrl+Enter Execute SQL
Ctrl+Space Auto-complete
Ctrl+F Find in results
Ctrl+E Export current view
Esc Clear selection

📊 Performance Comparison

vs Other Database Tools

Feature Adminer phpMyAdmin DBeaver MySQL Workbench
File Size ~400KB ~15MB ~150MB ~200MB
Installation 1 minute 15+ minutes 10+ minutes 15+ minutes
Multi-database ✅ ❌ (MySQL only) ✅ ❌ (MySQL only)
Web-based ✅ ✅ ❌ ❌
Resource Usage Very Low High Medium High
Learning Curve Easy Medium Medium Hard

🔒 Security Best Practices

Essential Security Measures

1. Rename the File

```bash
# Use a random name
mv adminer.php $(openssl rand -hex 12).php
```

2. IP Restriction (.htaccess)

```apache
<Files "secure-adminer.php">
    Order Deny,Allow
    Deny from all
    Allow from 192.168.1.0/24  # Local network
    Allow from 203.0.113.0     # Specific IP
</Files>
```

3. Basic Authentication

```apache
# Create .htpasswd file first
AuthType Basic
AuthName "Restricted Access"
AuthUserFile /path/to/.htpasswd
Require valid-user
```

4. HTTPS Enforcement

```apache
RewriteEngine On
RewriteCond %{HTTPS} off
RewriteRule ^(.*)$ https://%{HTTP_HOST}/$1 [R=301,L]
```

5. PHP Configuration

```php
// Add at top of adminer.php
ini_set('session.cookie_httponly', 1);
ini_set('session.use_only_cookies', 1);
ini_set('session.cookie_secure', 1);
```

Security Checklist

· Rename adminer.php to unique filename
· Use HTTPS only
· Implement IP whitelisting
· Add basic authentication
· Remove file after use
· Use strong passwords
· Enable 2FA if available
· Regular security updates
· Monitor access logs
· Disable when not needed

🎨 Customization

Themes

Adminer supports multiple visual themes:

Available official themes:

· Default - Clean and professional
· Pepa Linha - Dark sidebar, light content
· Mongo - MongoDB inspired
· Hidpi - High DPI displays
· Manago - Material design inspired

```php
// Load specific theme
// Download theme file and include
require_once('adminer.php');
require_once('themes/pepa-linha.php');
```

Custom CSS

Create adminer.css in the same directory:

```css
/* Custom styling */
body {
    font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;
}

#menu {
    background: #2c3e50;
    color: white;
}

#menu a {
    color: #ecf0f1;
}

#menu a:hover {
    background: #34495e;
}

.logout a {
    background: #e74c3c;
}
```

🔌 Plugins

Popular Plugins

1. Auto-login Plugin

```php
<?php
// auto-login.php
class AdminerAutoLogin {
    function login($login, $password) {
        return array(
            '127.0.0.1',  // server
            'username',    // username
            'password'     // password
        );
    }
}
```

2. Backup Plugin

```php
// Enable automatic backups
$plugins = array(
    new AdminerDumpJson(),
    new AdminerDumpXml(),
    new AdminerDumpZip(),
    new AdminerTablesFilter()
);
```

3. File Upload Plugin

```php
// Allow file uploads to BLOB fields
require_once('plugins/file-upload.php');
new AdminerFileUpload("BLOB");
```

How to Enable Plugins

```php
<?php
// Create index.php instead of using adminer.php directly
require_once('adminer.php');
require_once('plugins/plugin.php');

$plugins = array(
    new AdminerTablesFilter(),
    new AdminerDumpJson(),
    new AdminerFileUpload()
);

new AdminerPlugin($plugins);
```

⚙️ Advanced Configuration

PHP Configuration

Recommended PHP settings in php.ini:

```ini
; Performance
memory_limit = 256M
max_execution_time = 300
max_input_time = 300

; File uploads
post_max_size = 100M
upload_max_filesize = 100M
max_file_uploads = 20

; Session
session.gc_maxlifetime = 1440
session.cookie_lifetime = 0
session.use_strict_mode = 1
```

Custom Configuration File

Create adminer-config.php:

```php
<?php
function adminer_object() {
    class CustomAdminer extends Adminer {
        // Custom login credentials
        function credentials() {
            return array(
                getenv('DB_HOST') ?: 'localhost',
                getenv('DB_USER') ?: 'root',
                getenv('DB_PASS') ?: ''
            );
        }
        
        // Custom database name
        function database() {
            return getenv('DB_NAME') ?: 'test';
        }
        
        // Hide some databases
        function databases($flush = true) {
            $databases = parent::databases($flush);
            return array_diff($databases, ['information_schema', 'performance_schema']);
        }
        
        // Custom table name
        function tableName($tableStatus) {
            return $tableStatus['Name'];
        }
    }
    
    return new CustomAdminer;
}

require_once('adminer.php');
```

Environment Variables

```bash
# .env file
DB_HOST=mysql.example.com
DB_USER=admin
DB_PASS=secure_password
DB_NAME=production_db
ADMINER_DESIGN=pepa-linha
```

📝 Command Line Usage

Export Database

```bash
# Export using PHP
php adminer.php export > backup.sql

# With specific format
php adminer.php export --format=json > backup.json
```

Import Database

```bash
# Import SQL file
php adminer.php import < backup.sql
```

🐛 Troubleshooting

Common Issues and Solutions

1. "Cannot connect to database"

· Check database server is running
· Verify credentials
· Check firewall settings
· Test connection via command line

2. Blank page

· Enable PHP error reporting
· Check PHP version (7.4+ required)
· Verify file permissions
· Check error logs

3. Upload fails

```ini
; Increase limits in php.ini
post_max_size = 200M
upload_max_filesize = 200M
```

4. Slow performance

· Optimize database queries
· Add indexes
· Increase memory limit
· Use caching

Debug Mode

```php
<?php
// Enable debugging
error_reporting(E_ALL);
ini_set('display_errors', 1);

// Add to adminer.php
define('ADMINER_DEBUG', true);
```

· Plugin developers
· Community testers













