# Santhosh Reddy Pilli — Portfolio Website
## Deployment Guide

---

## Option A: Instant Deploy (No framework needed)

The `portfolio.html` file is a fully self-contained, production-ready website.
Upload it directly to any static host.

### Deploy to GitHub Pages (Free)
```bash
# 1. Create a new GitHub repo named: santhoshreddypilli.github.io
# 2. Upload portfolio.html and rename it to index.html
git init
git add portfolio.html
git mv portfolio.html index.html
git commit -m "Initial portfolio"
git remote add origin https://github.com/santhoshreddypilli/santhoshreddypilli.github.io.git
git push -u origin main
# Site live at: https://santhoshreddypilli.github.io
```

### Deploy to Netlify (Free, Instant)
1. Go to https://app.netlify.com/drop
2. Drag and drop portfolio.html
3. Rename to index.html in Netlify settings
4. Get a live URL instantly (e.g. https://amazing-site-12345.netlify.app)
5. Add a custom domain under Site Settings → Domain management

### Deploy to Vercel (Free)
```bash
npm i -g vercel
# Put index.html in a folder
mkdir portfolio && cp portfolio.html portfolio/index.html
cd portfolio
vercel --prod
# Follow prompts — live in 60 seconds
```

---

## Option B: Next.js App (For React ecosystem / future expansion)

### Prerequisites
- Node.js 18+
- npm or yarn

### Setup
```bash
npx create-next-app@latest santhosh-portfolio \
  --typescript --tailwind --eslint --app --src-dir
cd santhosh-portfolio
npm run dev
# → http://localhost:3000
```

### Project structure for Next.js
```
santhosh-portfolio/
├── src/
│   └── app/
│       ├── layout.tsx        # Root layout, fonts, metadata
│       ├── page.tsx          # Home page (wraps all sections)
│       └── globals.css       # CSS variables + base styles
├── components/
│   ├── Nav.tsx
│   ├── Hero.tsx
│   ├── About.tsx
│   ├── Education.tsx
│   ├── Certifications.tsx
│   ├── Skills.tsx
│   ├── Projects.tsx
│   ├── Blog.tsx
│   ├── Roadmap.tsx
│   ├── Resume.tsx
│   └── Contact.tsx
└── public/
    └── resume.pdf            # Your actual resume
```

### Deploy Next.js to Vercel
```bash
npm run build
vercel --prod
# Or connect your GitHub repo at vercel.com for auto-deploy on push
```

### Deploy Next.js to GitHub Pages
```bash
# Install gh-pages
npm install --save-dev gh-pages

# Add to next.config.js:
# output: 'export', basePath: '/repo-name'

# Add to package.json scripts:
# "export": "next build && next export",
# "deploy": "npm run export && gh-pages -d out"

npm run deploy
```

---

## Customisation Checklist

Before publishing, update these in `portfolio.html`:

| Item | Location | Action |
|------|----------|--------|
| Email | `mailto:` links | Replace with your real email |
| LinkedIn URL | 3 places | Update with your profile slug |
| GitHub URL | 3 places | Update with your username |
| Resume PDF | `href="#"` on Download buttons | Replace with actual PDF path |
| Blog links | `href="#"` on Read buttons | Replace with real posts / Medium links |
| Project links | `href="#"` on View Details | Link to GitHub repos or detailed pages |
| Location | Contact section | Update city/state if needed |

---

## Performance Notes

- **No JS frameworks** = instant first paint
- Fonts loaded from Google Fonts (preconnected)
- All SVGs inline = zero image requests
- Animations respect `prefers-reduced-motion`
- Fully accessible (ARIA labels, keyboard nav, focus states)
- Lighthouse score estimate: 95+ Performance, 100 Accessibility

---

## Adding Real Content

### Blog posts
Create a `/blog` directory and link each post, or use:
- **Medium** → link externally
- **Hashnode** → free dev blog with custom domain
- **Notion** → use Notion as a CMS, embed pages

### Project screenshots
Replace the SVG visuals in the `.project-visual` divs with:
```html
<img src="/images/project-1.png" alt="F1 Lap Time Prediction chart" />
```

### Google Analytics
Add before `</head>`:
```html
<!-- Google tag (gtag.js) -->
<script async src="https://www.googletagmanager.com/gtag/js?id=G-XXXXXXXXXX"></script>
<script>
  window.dataLayer = window.dataLayer || [];
  function gtag(){dataLayer.push(arguments);}
  gtag('js', new Date());
  gtag('config', 'G-XXXXXXXXXX');
</script>
```

---

## Contact Form Backend (Optional)

To make the contact form actually send emails, use one of:

**Formspree (Free, Easy)**
```html
<form action="https://formspree.io/f/YOUR_FORM_ID" method="POST">
```

**EmailJS (Free tier)**
```js
emailjs.sendForm('service_id', 'template_id', '#contactForm', 'public_key');
```

**Netlify Forms (Free if hosted on Netlify)**
```html
<form name="contact" netlify>
```

---

Good luck on the path to Formula 1. 🏁
