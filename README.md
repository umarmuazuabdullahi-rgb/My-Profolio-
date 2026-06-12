# MyPortfolio - Complete Portfolio System with Firebase

A fully responsive portfolio website with an integrated admin dashboard, built with HTML, Tailwind CSS, and Firebase.

## Features

### Public Portfolio
- **Home/Hero Section** - Display your name, title, profile photo, and social links
- **About Section** - Bio, skills with progress bars, and about photo
- **Projects Gallery** - Showcase projects with images, categories, descriptions, and links
- **Contact Form** - Visitors can send messages directly to your Firebase database

### Admin Dashboard
- **Dashboard** - Overview stats (total projects, new messages, site visits, pending tasks)
- **Projects Management** - Add, edit, delete projects with image upload support
- **Messages Inbox** - View, mark as read/unread, and delete contact messages
- **Settings** - Update profile information, photos, social links, and skills

### Responsive Design
- **Desktop** - Fixed sidebar navigation with full table views
- **Tablet** - Collapsible sidebar with optimized layouts
- **Mobile (Android/iOS)** - Bottom tab navigation with card-based project views
- **Touch Gestures** - Swipe to open/close sidebar, touch-friendly buttons (44px min)
- **Safe Area Support** - Works with notched phones (iPhone X+, modern Android)

## Technology Stack

| Technology | Purpose |
|------------|---------|
| HTML5 | Structure |
| Tailwind CSS | Styling (via CDN) |
| Font Awesome | Icons |
| Firebase Authentication | Admin login |
| Firebase Realtime Database | Data storage |
| Firebase Storage | Image storage (optional) |

## Setup Instructions

### 1. Create a Firebase Project

1. Go to [Firebase Console](https://console.firebase.google.com/)
2. Click "Add Project" and follow the setup
3. Enable **Authentication** (Email/Password provider)
4. Create **Realtime Database** and set rules:

```json
{
  "rules": {
    "portfolio": {
      ".read": true,
      ".write": "auth != null"
    }
  }
}
```

5. Register a web app and copy your Firebase config

### 2. Configure the Project

Open `profolio-firebase-complete.html` and replace the Firebase config:

```javascript
const firebaseConfig = {
    apiKey: "YOUR_API_KEY",
    authDomain: "YOUR_PROJECT_ID.firebaseapp.com",
    databaseURL: "https://YOUR_PROJECT_ID-default-rtdb.firebaseio.com",
    projectId: "YOUR_PROJECT_ID",
    storageBucket: "YOUR_PROJECT_ID.appspot.com",
    messagingSenderId: "YOUR_SENDER_ID",
    appId: "YOUR_APP_ID"
};
```

### 3. Create Admin Account

1. In Firebase Console, go to **Authentication > Users**
2. Click "Add User"
3. Enter email and password for admin access
4. Use these credentials to log into the admin panel

### 4. Deploy

Simply open the HTML file in any modern web browser, or deploy to:
- Firebase Hosting
- GitHub Pages
- Netlify
- Vercel
- Any static hosting

## File Structure

```
profolio-firebase-complete.html    # Main file (everything in one file)
```

> **Note:** This is a single-file application. All HTML, CSS, and JavaScript are contained in one file for easy deployment.

## Database Structure

```
portfolio/
  profile/
    name: string
    title: string
    bio: string
    email: string
    phone: string
    location: string
    profileImage: string (base64)
    aboutImage: string (base64)
    social/
      github: string
      linkedin: string
      twitter: string
      instagram: string
    skills/
      [skillId]/
        name: string
        level: number (0-100)
  projects/
    [projectId]/
      title: string
      category: string
      description: string
      link: string
      image: string (base64 or URL)
      createdAt: timestamp
  messages/
    [messageId]/
      name: string
      email: string
      subject: string
      message: string
      timestamp: timestamp
      read: boolean
```

## Admin Panel Navigation

### Desktop (1024px+)
- Fixed left sidebar with all navigation links
- Full-width tables for projects and messages

### Tablet (768px - 1023px)
- Collapsible sidebar with overlay
- Responsive tables with horizontal scroll

### Mobile (< 768px)
- Bottom tab bar navigation (4 tabs)
- Card-based project list
- Swipe from left edge to open sidebar
- All forms optimized for touch input

## Keyboard Shortcuts

| Shortcut | Action |
|----------|--------|
| ESC | Close modals and sidebar |
| Swipe Left (on sidebar) | Close sidebar (mobile) |
| Swipe Right (from edge) | Open sidebar (mobile) |

## Browser Support

- Chrome 90+
- Firefox 88+
- Safari 14+
- Edge 90+
- Samsung Internet 14+
- iOS Safari 14+

## Customization

### Colors
Edit the Tailwind config in the `<script>` tag:
```javascript
tailwind.config = {
    theme: {
        extend: {
            colors: { 
                primary: '#3b82f6',    // Change this
                secondary: '#64748b',
                dark: '#0f172a'
            }
        }
    }
}
```

### Fonts
The default font is **Inter** from Google Fonts. Change it by updating the `<link>` tag in the `<head>`.

## Troubleshooting

### Dashboard shows blank
- Ensure Firebase config is correct
- Check browser console for errors
- Verify database rules allow read/write

### Images not uploading
- Images are stored as base64 in Realtime Database
- Maximum recommended size: 5MB per image
- For production, consider using Firebase Storage

### Mobile menu not working
- Ensure JavaScript is enabled
- Check that Tailwind CSS CDN is loading
- Try refreshing the page

## License

MIT License - Free for personal and commercial use.

## Credits

- [Tailwind CSS](https://tailwindcss.com/)
- [Font Awesome](https://fontawesome.com/)
- [Firebase](https://firebase.google.com/)
- [Google Fonts - Inter](https://fonts.google.com/specimen/Inter)
