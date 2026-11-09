# SINAWEY | سيناوي

متجر عربي (RTL) لمنتجات سيناء الأصيلة — زيت زيتون وعجوة سيناء — مبني بـ React + Vite.
الطلب يتم عبر واتساب فقط، ولا توجد أسعار ولا دفع إلكتروني في أي مكان.

> Arabic RTL e-commerce site for SINAWEY (Sinai olive oil & Ajwa dates). Orders go through WhatsApp only: **+201050925066**. No prices, no online payment.

## المميزات | Features

- تصميم عربي كامل من اليمين لليسار (RTL) بهوية سيناوية فاخرة
- منتجان: زيت زيتون سيناء، وعجوة سيناء (بدون أسعار)
- زر «اطلب الآن» يفتح واتساب برسالة عربية جاهزة
- سلة طلب ترسل الطلب كاملاً عبر واتساب
- بحث وتصفية للمنتجات
- متجاوب مع الجوال والتابلت والحاسوب
- تحسينات SEO وإتاحة (Accessibility)

## المتطلبات | Requirements

- Node.js 18 أو أحدث
- npm (يأتي مع Node.js)

## التثبيت والتشغيل | Installation

```bash
git clone <your-repo-url>
cd sinawey
npm install
npm run dev
```

ثم افتح الرابط الذي يظهر في الطرفية (عادة `http://localhost:5173`).

| الأمر | الوظيفة |
| --- | --- |
| `npm run dev` | تشغيل نسخة التطوير |
| `npm run build` | بناء نسخة الإنتاج في مجلد `dist/` |
| `npm run preview` | معاينة نسخة الإنتاج محلياً |

## الرفع على GitHub | Upload to GitHub

```bash
git init
git add .
git commit -m "Initial commit: SINAWEY website"
git branch -M main
git remote add origin https://github.com/<username>/<repo>.git
git push -u origin main
```

## النشر | Deployment

الأمر `npm run build` ينتج مجلد `dist/` وهو موقع ثابت (static) يمكن استضافته في أي مكان.

### Netlify
1. اربط مستودع GitHub من لوحة Netlify (Add new site → Import from Git).
2. Build command: `npm run build`
3. Publish directory: `dist`

### Vercel
1. Import Project من GitHub.
2. Framework Preset: **Vite** (يُكتشف تلقائياً).
3. Build command: `npm run build` — Output directory: `dist`

### Cloudflare Pages
1. Create a project → Connect to Git.
2. Build command: `npm run build` — Build output directory: `dist`

### GitHub Pages
1. في `vite.config.js` أضف `base` باسم المستودع:
   ```js
   export default defineConfig({
     base: '/<repo-name>/',
     plugins: [react()],
   });
   ```
2. نفّذ `npm run build` ثم انشر محتويات مجلد `dist/` (مثلاً عبر GitHub Actions أو فرع `gh-pages`).

## هيكل المشروع | Project structure

```
sinawey/
├── index.html
├── package.json
├── vite.config.js
├── README.md
├── .gitignore
├── public/
│   ├── favicon.svg
│   ├── robots.txt
│   └── images/            (hero, olive-oil-1/2, dates-1/2 — SVG)
└── src/
    ├── main.jsx
    ├── App.jsx
    ├── config.js          اسم العلامة ورقم واتساب (مكان واحد للتعديل)
    ├── data/products.js   المنتجات والتصنيفات والآراء الحقيقية
    ├── utils/whatsapp.js  روابط واتساب والرسائل العربية
    ├── context/CartContext.jsx
    ├── hooks/useReveal.js
    ├── components/        مكونات الصفحة
    └── styles/global.css
```

## واتساب | WhatsApp

- زر «اطلب الآن» يفتح `https://wa.me/201050925066` برسالة عربية جاهزة تتضمن التحية واسم المنتج.
- من السلة يُرسل الطلب كاملاً (أسماء المنتجات والكميات) في رسالة واحدة.
- لتغيير الرقم عدّل `src/config.js` فقط.

## قبل الإطلاق | Before launch

1. **الصور:** الصور الحالية رسومات SVG بهوية العلامة وليست صوراً فوتوغرافية. استبدلها بصور منتجاتكم الحقيقية
   بوضع الملفات في `public/images/` وتحديث مسارات `images` في `src/data/products.js`.
2. **آراء العملاء:** القسم لا يعرض أي آراء مختلقة. أضف آراء حقيقية (بإذن أصحابها) إلى مصفوفة
   `testimonials` في `src/data/products.js` وستظهر تلقائياً.
3. **تفاصيل المنتجات:** راجع نصوص التفاصيل في `src/data/products.js` وأضف الأحجام والعبوات المتاحة إن رغبتم.
4. **SEO:** بعد معرفة النطاق، أضف وسم `canonical` و`sitemap.xml` وصورة معاينة (OG) بصيغة PNG/JPG بدل SVG.
