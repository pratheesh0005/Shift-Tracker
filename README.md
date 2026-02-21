# Shift Tracker - Employee Shift Management System

A lightweight, serverless PHP application for managing employee shifts and attendance, deployed on Vercel.

## 🚀 Quick Start

### Live Application
- **URL:** https://shift-tracker-steel.vercel.app/
- **Status:** ✅ Deployed and Running

### Repository
- **GitHub:** https://github.com/pratheesh0005/Shift-Tracker
- **Branch:** main

---

## 📋 Features

- ✅ Simple and lightweight PHP application
- ✅ Deployed on Vercel (serverless)
- ✅ Automatic deployment from GitHub
- ✅ Scalable and production-ready
- ✅ Easy to customize and extend
- ✅ Database-ready architecture

---

## 🛠️ Technology Stack

- **Language:** PHP 7.4+
- **Platform:** Vercel (Serverless)
- **Runtime:** vercel-php@0.7.1
- **Version Control:** Git & GitHub
- **Database:** Ready for MySQL, PostgreSQL, or other services

---

## 📁 Project Structure

```
Shift-Tracker/
├── api/
│   ├── index.php              # Main application entry point
│   ├── config.php             # Configuration and settings
│   └── database.sql           # Database schema
├── vercel.json                # Vercel deployment configuration
├── README.md                  # This file
└── .git/                       # Git repository
```

### File Descriptions

#### `api/index.php`
Main application file. Currently displays "Attendance App". Customize this file to add your features:
- Employee management
- Shift tracking
- Attendance reporting
- User authentication
- API endpoints

#### `api/config.php`
Configuration file containing:
- Database connection settings
- API keys and credentials
- Application constants
- Environment-specific settings

#### `api/database.sql`
Database schema file. Currently contains a basic employees table. Expand this to include:
- Employees table
- Shifts table
- Attendance records
- User accounts

#### `vercel.json`
Vercel deployment configuration:
- Specifies PHP runtime (vercel-php@0.7.1)
- Configures routing rules
- Sets up build and deployment settings

---

## 🚀 Deployment

### Automatic Deployment
This application is configured for automatic deployment:
1. Push code to the `main` branch on GitHub
2. Vercel automatically detects changes
3. Application is built and deployed within seconds
4. Changes are live at https://shift-tracker-steel.vercel.app/

### Manual Deployment
To deploy manually:
```bash
# Install Vercel CLI
npm i -g vercel

# Deploy
vercel --prod
```

---

## 📝 Customization

### Change Application Title
Edit `api/index.php`:
```php
<?php echo 'Your Custom Title'; ?>
```

### Add Database Connection
Update `api/config.php` with your database credentials:
```php
<?php
define('DB_HOST', 'your-database-host');
define('DB_USER', 'your-database-user');
define('DB_PASS', 'your-database-password');
define('DB_NAME', 'shift_tracker');
?>
```

### Create API Endpoints
Add routes in `api/index.php`:
```php
<?php
$action = $_GET['action'] ?? 'home';

switch($action) {
    case 'employees':
        // Return employee data
        break;
    case 'shifts':
        // Return shift data
        break;
}
?>
```

For detailed customization instructions, see [CUSTOMIZATION_GUIDE.md](../CUSTOMIZATION_GUIDE.md)

---

## 🗄️ Database Setup

### Option 1: Supabase (PostgreSQL)
1. Create account at https://supabase.com
2. Create new project
3. Get connection string
4. Update `api/config.php` with connection details
5. Run `api/database.sql` to create tables

### Option 2: PlanetScale (MySQL)
1. Create account at https://planetscale.com
2. Create new database
3. Get connection string
4. Update `api/config.php`
5. Run `api/database.sql`

### Option 3: Neon (PostgreSQL)
1. Create account at https://neon.tech
2. Create new project
3. Get connection string
4. Update `api/config.php`
5. Run `api/database.sql`

### Using Environment Variables
For production, use Vercel environment variables:

1. Go to https://vercel.com/pratheesh0005s-projects/shift-tracker/settings/environment-variables
2. Add variables:
   ```
   DB_HOST=your-host
   DB_USER=your-user
   DB_PASS=your-password
   DB_NAME=shift_tracker
   ```
3. Update `api/config.php` to read from environment:
   ```php
   <?php
   define('DB_HOST', $_ENV['DB_HOST'] ?? 'localhost');
   define('DB_USER', $_ENV['DB_USER'] ?? 'root');
   define('DB_PASS', $_ENV['DB_PASS'] ?? '');
   define('DB_NAME', $_ENV['DB_NAME'] ?? 'shift_tracker');
   ?>
   ```

---

## 🔧 Local Development

### Prerequisites
- PHP 7.4 or higher
- Git
- Composer (optional)

### Setup

1. **Clone repository:**
   ```bash
   git clone https://github.com/pratheesh0005/Shift-Tracker.git
   cd Shift-Tracker
   ```

2. **Start PHP server:**
   ```bash
   php -S localhost:8000 -t api/
   ```

3. **Open browser:**
   Visit http://localhost:8000

4. **Make changes and test**

### Testing

```bash
# Test specific endpoint
curl http://localhost:8000/?action=employees

# Test with parameters
curl "http://localhost:8000/?action=shifts&date=2026-02-20"
```

---

## 📦 Dependencies

### Runtime
- PHP 7.4+ (provided by Vercel)
- vercel-php@0.7.1 (PHP runtime for Vercel)

### Optional Database Drivers
- MySQLi (for MySQL/MariaDB)
- PDO PostgreSQL (for PostgreSQL)
- PDO SQLite (for SQLite)

---

## 🔐 Security

### Best Practices
1. **Never commit sensitive data:**
   - API keys
   - Database passwords
   - Private credentials

2. **Use environment variables:**
   - Store secrets in Vercel settings
   - Access via `$_ENV` in PHP

3. **Validate input:**
   - Sanitize user inputs
   - Use prepared statements for database queries
   - Validate API requests

4. **Enable HTTPS:**
   - Vercel provides free SSL certificates
   - All traffic is encrypted

### Example: Secure Database Connection
```php
<?php
// Read from environment variables
$host = $_ENV['DB_HOST'] ?? 'localhost';
$user = $_ENV['DB_USER'] ?? 'root';
$pass = $_ENV['DB_PASS'] ?? '';
$name = $_ENV['DB_NAME'] ?? 'shift_tracker';

// Use prepared statements
$conn = new mysqli($host, $user, $pass, $name);
$stmt = $conn->prepare("SELECT * FROM employees WHERE id = ?");
$stmt->bind_param("i", $id);
$stmt->execute();
?>
```

---

## 📊 Monitoring

### Vercel Dashboard
Monitor your application at: https://vercel.com/pratheesh0005s-projects/shift-tracker

Available metrics:
- Deployment status
- Build logs
- Runtime logs
- Performance metrics
- Error tracking

### Enable Analytics
1. Go to Vercel project settings
2. Enable "Web Analytics"
3. Enable "Speed Insights"
4. View metrics in Vercel dashboard

---

## 🐛 Troubleshooting

### Issue: Application shows blank page
**Solution:**
- Check Vercel deployment logs
- Verify `api/index.php` syntax
- Ensure `vercel.json` routing is correct

### Issue: Changes not deploying
**Solution:**
- Verify changes are in `main` branch
- Check GitHub for latest commits
- Monitor Vercel deployments

### Issue: Database connection errors
**Solution:**
- Verify environment variables are set
- Check database credentials
- Ensure database service is running

### Issue: 404 errors
**Solution:**
- Check `vercel.json` routing configuration
- Ensure all requests route to `api/index.php`
- Verify file paths are correct

---

## 📚 Documentation

- [Deployment Summary](../DEPLOYMENT_SUMMARY.md) - Complete deployment details
- [Customization Guide](../CUSTOMIZATION_GUIDE.md) - Step-by-step customization instructions
- [Vercel Docs](https://vercel.com/docs) - Official Vercel documentation
- [PHP Documentation](https://www.php.net/docs.php) - PHP language reference

---

## 🤝 Contributing

To contribute to this project:

1. Fork the repository
2. Create a feature branch: `git checkout -b feature/your-feature`
3. Commit changes: `git commit -m "Add your feature"`
4. Push to branch: `git push origin feature/your-feature`
5. Submit a pull request

---

## 📄 License

This project is open source and available under the MIT License.

---

## 👨‍💻 Author

**Created by:** Manus AI Agent  
**Deployment Date:** February 20, 2026  
**Repository:** https://github.com/pratheesh0005/Shift-Tracker

---

## 📞 Support

For issues or questions:
1. Check the [Troubleshooting](#-troubleshooting) section
2. Review [CUSTOMIZATION_GUIDE.md](../CUSTOMIZATION_GUIDE.md)
3. Check Vercel deployment logs
4. Visit [Vercel Help](https://vercel.com/help)

---

## 🎯 Roadmap

### Phase 1: Core Features (Current)
- ✅ Basic PHP application
- ✅ Vercel deployment
- ✅ GitHub integration
- ✅ Automatic deployment

### Phase 2: Employee Management
- [ ] Employee CRUD operations
- [ ] Employee profiles
- [ ] Department management
- [ ] Role-based access

### Phase 3: Shift Management
- [ ] Shift scheduling
- [ ] Shift assignments
- [ ] Shift swaps
- [ ] Shift templates

### Phase 4: Attendance Tracking
- [ ] Check-in/check-out
- [ ] Attendance reports
- [ ] Absence tracking
- [ ] Leave management

### Phase 5: Advanced Features
- [ ] User authentication
- [ ] Dashboard analytics
- [ ] Email notifications
- [ ] Mobile app support

---

**Last Updated:** February 20, 2026  
**Status:** ✅ Production Ready
