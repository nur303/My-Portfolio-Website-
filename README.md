# Nur Muhammad Portfolio - Design Specification

## Concept & Vision

A dark, premium portfolio that feels like stepping into a digital art installation. The experience is cinematic—every scroll reveals content with deliberate theatricality. The site communicates technical mastery through its own construction: smooth as silk, responsive as intuition, and visually striking without being garish. It's the digital equivalent of a perfectly tailored black suit.

## Design Language

### Aesthetic Direction
**Reference**: High-end creative agency meets luxury tech brand. Think Stripe's elegance crossed with Awwwards-selected portfolios. Dark, confident, with moments of electric accent color that feel like sparks in darkness.

### Color Palette
- **Background**: `#0a0a0b` (near-black with subtle blue undertone)
- **Surface**: `#121214` (elevated dark surfaces)
- **Border/Subtle**: `#1a1a1f` (soft boundaries)
- **Text Primary**: `#fafafa` (crisp white)
- **Text Secondary**: `#888893` (muted descriptions)
- **Accent Primary**: `#6366f1` (electric indigo)
- **Accent Glow**: `#818cf8` (lighter indigo for hovers/glows)
- **Accent Secondary**: `#22d3ee` (cyan spark for highlights)

### Typography
- **Headings**: "Space Grotesk" - geometric, modern, confident
- **Body**: "Inter" - clean, highly readable at all sizes
- **Monospace accents**: "JetBrains Mono" - for code/tech elements

### Spatial System
- Base unit: 8px
- Section padding: 120px vertical (desktop), 80px (mobile)
- Content max-width: 1400px
- Card gaps: 32px
- Generous whitespace creates breathing room

### Motion Philosophy
- **Entrance**: Elements fade up from below with staggered timing (60-100ms delays)
- **Scroll-linked**: Parallax layers at 0.3x, 0.5x, 0.7x speeds
- **Hover states**: Magnetic pulls, subtle scale (1.02x), glow intensification
- **Cursor**: Morphing states - default dot, larger ring on interactive, text cursor on links
- **Page transitions**: Content reveals tied to scroll progress, never jarring
- **Timing**: Custom bezier curves `cubic-bezier(0.16, 1, 0.3, 1)` for smooth deceleration

### Visual Assets
- **Icons**: Phosphor Icons (thin weight for elegance)
- **Decorative**: CSS gradient orbs, subtle noise texture overlay, geometric grid patterns
- **Project images**: Gradient placeholders with project initials, CSS-based abstract visuals

## Layout & Structure

### Page Flow
1. **Hero** (100vh) - Immersive intro with name/title/portrait, social links, CTA
2. **About** (auto) - Personal narrative with scroll-triggered line reveals
3. **Skills** (auto) - Floating grid with hover interactions
4. **Projects** (auto) - Large immersive cards with hover transformations
5. **Education** (auto) - Vertical timeline with subtle animations
6. **Contact** (auto) - Form + details with footer

### Responsive Strategy
- Desktop: Full experience with all effects
- Tablet (≤1024px): Reduced parallax, simplified background
- Mobile (≤768px): Essential animations only, stacked layouts, touch-optimized

### Navigation
- Fixed minimal header (logo left, nav right)
- Nav links with magnetic hover effect
- Progress indicator (subtle line at top)

## Features & Interactions

### Custom Cursor
- **Default**: Small dot (8px) with trailing effect
- **Interactive elements**: Expands to ring (40px) with "VIEW" text inside
- **Links**: Cursor becomes crosshair
- **Smooth follow**: Uses lerp for organic movement

### Smooth Scrolling
- Lenis library for buttery-smooth momentum
- GSAP ScrollTrigger for scroll-linked animations

### Hero Section
- Text stagger animation on load (name → role → details)
- Portrait with subtle floating animation
- Social icons with magnetic hover
- "View My Work" CTA with magnetic pull effect + ripple on click

### About Section
- Text reveals line-by-line as scrolling into view
- Background subtle gradient shift
- Counter animation for key stats (if added)

### Skills Section
- Marquee ticker for skill categories
- Floating grid cards with 3D tilt on hover
- Each skill has icon + label with glow effect

### Projects Section
- Cards expand on hover (scale + shadow lift)
- Background color shifts per card
- "View Project" link appears on hover with slide animation
- Staggered entrance as section scrolls into view

### Education Section
- Timeline with connecting line that draws as scrolling
- Cards slide in from alternating sides
- Certifications have subtle badge styling

### Contact Section
- Form fields with floating labels
- Focus states with gradient borders
- Submit button with loading state animation
- Social links with hover glow

## Component Inventory

### Header
- States: Transparent (top), Solid (scrolled)
- Logo: Text-based, hover glow
- Nav items: Hover underline animation

### Hero CTA Button
- Default: Gradient background, rounded
- Hover: Magnetic pull toward cursor, scale 1.05
- Active: Ripple effect from click point
- Loading: Spinner animation (if needed)

### Project Card
- Default: Dark surface, subtle border
- Hover: Lift (translateY -8px), shadow expansion, background gradient shift, content reveal

### Skill Card
- Default: Subtle glow border
- Hover: 3D tilt (perspective transform), intensified glow

### Timeline Item
- Default: Connected by line
- Reveal: Line draws, then card fades in

### Form Input
- Default: Dark background, subtle border
- Focus: Gradient border glow, label floats up
- Error: Red border, shake animation
- Valid: Green checkmark

### Social Icon
- Default: Muted color
- Hover: Glow + scale, magnetic pull

## Technical Approach

### Libraries
- **GSAP** (3.12+): Core animation engine with ScrollTrigger
- **Lenis**: Smooth scroll with momentum
- **Three.js**: Optional particle background (CSS fallback if performance issues)
- **Phosphor Icons**: Icon system via CDN

### Performance Considerations
- Lazy load below-fold content
- Throttle scroll event handlers
- Use `will-change` sparingly
- GPU-accelerated transforms only

### Code Organization
- `index.html`: Semantic structure, component blocks clearly labeled
- `styles.css`: CSS custom properties, component styles, responsive breakpoints
- `script.js`: GSAP timeline, ScrollTrigger setup, cursor logic, form handling

### Browser Support
- Modern browsers (Chrome, Firefox, Safari, Edge latest 2 versions)
- Graceful degradation for older browsers
