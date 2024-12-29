# EdgeSync Solutions Website Documentation

<!-- ![EdgeSync Solutions](public/edgesync-logo.png) -->

## Table of Contents
- [Overview](#overview)
- [Features](#features)
- [Technology Stack](#technology-stack)
- [Project Structure](#project-structure)
- [Getting Started](#getting-started)
- [Development](#development)
- [Components](#components)
- [Routing](#routing)
- [State Management](#state-management)
- [API Integration](#api-integration)
- [Styling](#styling)
- [Performance Optimization](#performance-optimization)
- [Deployment](#deployment)
- [Contributing](#contributing)

## Overview

EdgeSync Solutions is a modern, responsive website built with React and Vite, showcasing our software services and solutions. The website features a clean, professional design with interactive elements and seamless user experience across all devices.

### Key Features
- 🎨 Modern, responsive design
- 🤖 AI-powered chat support using Google's Gemini API
- 📱 Mobile-first approach
- ⚡ Optimized performance
- 🎭 Smooth animations using Framer Motion
- 📝 Dynamic blog system
- 💼 Portfolio showcase
- 📞 Contact form integration

## Technology Stack

- **Frontend Framework:** React 18
- **Build Tool:** Vite
- **Styling:** Tailwind CSS
- **Animations:** Framer Motion
- **Icons:** Lucide React
- **Routing:** React Router DOM
- **AI Integration:** Google Generative AI
- **Date Handling:** date-fns
- **HTTP Client:** Axios

## Project Structure

```
edgesyncsolutions/
├── public/
│   ├── edgesync-logo.png
│   └── robots.txt
├── src/
│   ├── components/
│   │   ├── about/
│   │   ├── blog/
│   │   ├── chat/
│   │   ├── layout/
│   │   ├── portfolio/
│   │   ├── pricing/
│   │   ├── sections/
│   │   └── ui/
│   ├── data/
│   │   ├── blogData.js
│   │   ├── portfolioData.js
│   │   └── serviceData.js
│   ├── pages/
│   │   ├── services/
│   │   ├── portfolio/
│   │   └── [other pages]
│   ├── styles/
│   │   └── colors.js
│   ├── App.jsx
│   └── main.jsx
└── [config files]
```

## Getting Started

### Prerequisites
- Node.js (v16 or higher)
- npm or yarn

### Installation

```bash
# Clone the repository
git clone https://github.com/yourusername/edgesyncsolutions.git

# Navigate to project directory
cd edgesyncsolutions

# Install dependencies
npm install

# Start development server
npm run dev
```

## Development

### Available Scripts

```bash
# Start development server
npm run dev

# Build for production
npm run build

# Preview production build
npm run preview

# Lint code
npm run lint
```

## Components

### Core Components

1. **Layout Components**
   - `Header`: Main navigation component
   - `Footer`: Site footer with contact information
   - `Layout`: Base layout wrapper

2. **Section Components**
   - `Hero`: Landing page hero section
   - `Services`: Services showcase
   - `Portfolio`: Project portfolio
   - `Contact`: Contact form section

3. **Chat Components**
   - `GeminiChat`: AI-powered chat interface
   - `ChatInput`: Message input component
   - `ChatMessages`: Message display component

### Component Usage Example

```jsx
import { GeminiChat } from '../components/chat/GeminiChat';

function HomePage() {
  return (
    <div>
      <Hero />
      <Services />
      <Portfolio />
      <GeminiChat />
    </div>
  );
}
```

## Routing

The website uses React Router DOM for navigation. Routes are defined in `App.jsx`:

```jsx
<Routes>
  <Route element={<Layout />}>
    <Route path="/" element={<Home />} />
    <Route path="/blog" element={<Blog />} />
    <Route path="/blog/:slug" element={<BlogPost />} />
    <Route path="/about" element={<About />} />
    <Route path="/services/:slug" element={<ServiceDetail />} />
    <Route path="/services/:slug/pricing" element={<ServicePricing />} />
    <Route path="/portfolio/:id" element={<PortfolioDetail />} />
    <Route path="*" element={<NotFound />} />
  </Route>
</Routes>
```

## API Integration

### Gemini AI Integration

```javascript
const genAI = new GoogleGenerativeAI(GEMINI_API_KEY);

const sendMessage = async (text) => {
  const model = genAI.getGenerativeModel({ model: "gemini-pro" });
  const result = await model.generateContent(prompt);
  return result.response.text();
};
```

## Styling

### Tailwind Configuration

The project uses Tailwind CSS with custom configuration:

```javascript
// tailwind.config.js
export default {
  theme: {
    extend: {
      colors: {
        primary: '#23BAB3',
        'primary-dark': '#1E9E98',
        secondary: '#0C3C56',
        'secondary-dark': '#0A3247',
      },
      // ... other customizations
    },
  },
};
```

### CSS Organization

- Component-specific styles in `/src/components/*/styles/`
- Global styles in `/src/styles/`
- Utility classes through Tailwind

## Performance Optimization

1. **Code Splitting**
   - Route-based splitting
   - Component lazy loading

2. **Image Optimization**
   - Responsive images
   - Lazy loading
   - Optimal formats

3. **Build Optimization**
   ```javascript
   // vite.config.js
   export default defineConfig({
     build: {
       rollupOptions: {
         output: {
           manualChunks: {
             vendor: ['react', 'react-dom'],
             animations: ['framer-motion'],
           },
         },
       },
     },
   });
   ```

## Deployment

The website is configured for deployment on Netlify:

1. **Build Configuration**
   - Build command: `npm run build`
   - Publish directory: `dist`
   - Node version: 16+

2. **Environment Variables**
   ```env
   VITE_GEMINI_API_KEY=your_api_key
   ```


## Pages Documentation

### Home Page (`src/pages/Home.jsx`)
The main landing page component that integrates various sections:
```jsx
// Key components used:
- Hero: Landing section with animated text
- Services: Service offerings grid
- Portfolio: Project showcase
- Testimonials: Client testimonials
- Contact: Contact form
```

### About Page (`src/pages/About.jsx`)
Company information and team showcase:
```jsx
// Components:
- AboutHero: Hero section with company tagline
- AboutContent: Detailed company information
- AboutGrid: Visual grid of company values
- Expertise: Technical expertise showcase
- CallToAction: Calendly integration for consultations
```

### Blog Pages
#### Blog List (`src/pages/Blog.jsx`)
Blog listing page with features:
- Grid layout of blog posts
- Category filtering
- Responsive card design
- Animated transitions
- SEO optimization

#### Blog Post (`src/pages/BlogPost.jsx`)
Individual blog post page:
```jsx
// Features:
- Rich text content
- Author information
- Related posts
- Social sharing
- Reading time estimate
```

### Portfolio Pages
#### Portfolio Detail (`src/pages/portfolio/PortfolioDetail.jsx`)
Project showcase page:
```jsx
// Key features:
- Project gallery
- Technical details
- Challenge/Solution sections
- Related projects
- Interactive demo links
```

### Service Pages
#### Service Detail (`src/pages/services/ServiceDetail.jsx`)
Individual service page with:
```jsx
// Components:
- Feature list
- Benefits section
- Case studies
- Integration examples
- Technical specifications
```

#### Service Pricing (`src/pages/services/ServicePricing.jsx`)
Pricing page features:
```jsx
// Key elements:
- Pricing tiers
- Feature comparison
- Custom quotes
- Payment methods
- FAQ section
```

### Error Page (`src/pages/404.jsx`)
Custom 404 error page:
```jsx
// Features:
- Friendly error message
- Navigation suggestions
- Search functionality
- Return to home button
```

## Page-Specific Features

### Home Page Features
- Animated hero section with rotating text
- Service cards with hover effects
- Portfolio grid with filtering
- Testimonial carousel
- Contact form with validation

### About Page Features
- Team member profiles
- Company timeline
- Mission and values
- Office locations
- Client logos

### Blog Features
- Category-based filtering
- Search functionality
- Pagination
- Author profiles
- Comment system
- Share buttons

### Portfolio Features
- Project filtering
- Image galleries
- Video integration
- Technical specifications
- Client testimonials

### Service Pages Features
- Feature comparison tables
- Integration diagrams
- Case study showcase
- ROI calculators
- FAQ accordions

## Page Optimization

### SEO Optimization
Each page includes:
```jsx
// Meta tags
<meta name="description" content="..." />
<meta name="keywords" content="..." />
<meta property="og:title" content="..." />
<meta property="og:description" content="..." />
```

### Performance
- Lazy loading of images
- Code splitting per route
- Optimized asset delivery
- Caching strategies
- Performance monitoring

### Accessibility
- ARIA labels
- Keyboard navigation
- Screen reader support
- Color contrast compliance
- Focus management

### Mobile Optimization
- Responsive layouts
- Touch-friendly interfaces
- Mobile-first design
- Optimized images
- Performance budgets
