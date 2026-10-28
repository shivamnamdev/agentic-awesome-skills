---
name: animated-github-profile
description: Comprehensive blueprint for designing, animating, and deploying high-impact, cinematic GitHub profile READMEs using pure SVG, CSS, SMIL, and GitHub Actions. Covers interactive camera HUD viewfinders, walking vector mascots, dual-panel stories carousels with timer bars, tech orbits, lanyard & live telemetry KPI dashboards, dual 3D skyline + snake contribution graphs, and animated connect cards.
license: MIT
metadata:
  version: 2.0.0
  author: Shivam Namdev
  tags:
    - github
    - profile-readme
    - svg-animation
    - smil
    - css-animation
    - telemetry-dashboard
    - portfolio
---

# Animated GitHub Profile Master Skill

A complete engineering guide and agent instruction set for designing, generating, and deploying cinematic GitHub profile READMEs that bypass GitHub's JavaScript restrictions using pure SVG, CSS `@keyframes`, SMIL animations, and automated GitHub Actions workflows.

---

## Why Pure SVG Animations?

1. **GitHub Security Model**: GitHub sanitizes all Markdown files on render, stripping out `<script>` tags, inline JS, and iframes. Modern motion libraries (Framer Motion, GSAP, Three.js) cannot run in a GitHub README.
2. **Native SVG Motion**: Standalone SVGs containing embedded `<style>` blocks with `@keyframes` and SMIL elements (`<animate>`, `<animateTransform>`) are natively rendered by all modern browsers without external runtime dependencies.
3. **Zero Third-Party Downtime**: Unlike external status generators (e.g., `github-readme-stats`, `shields.io`) that frequently fail or display broken images when GitHub API rate-limits are exceeded, self-contained SVGs committed directly to the profile repository render with 100% reliability.

---

## The 7-Tier Master Architecture

The state-of-the-art animated profile (as implemented on `github.com/shivamnamdev`) uses a responsive 7-tier vertical stack:

```
┌────────────────────────────────────────────────────────────────────────┐
│ 1. HERO VIEWFINDER HUD & WALKING MASCOT (hero.svg)                     │
│    - Camera HUD framing, REC blinking indicator, timecode & 4K badge   │
│    - Dynamic audio equalizer bars & scrubbing playhead                 │
│    - Multi-stop shimmer gradient name & cycling role headlines         │
│    - Multi-joint animated vector mascot (walking cycle + salute/wave)  │
├────────────────────────────────────────────────────────────────────────┤
│ 2. WHAT I BUILD & LIFE BEYOND CODE (about-life.svg)                    │
│    - Left: Browser window with URL pill, typing cursor & core features │
│    - Right: Automated Instagram-style 3-slide story carousel           │
│      (MMA/Combat, Philosophy, Travel) with timer progress bars & rings │
├────────────────────────────────────────────────────────────────────────┤
│ 3. 3D TECH ORBIT & ARCHITECTURAL PILLARS (stack.svg)                   │
│    - Glowing core specialization surrounded by multi-speed orbits      │
│    - Satellites revolving along elliptical orbital paths               │
│    - Capability matrix detailing architectural experience metrics      │
├────────────────────────────────────────────────────────────────────────┤
│ 4. DEVELOPER ID & LIVE TELEMETRY DASHBOARD (id-dashboard.svg)          │
│    - Left: Realistic swinging lanyard badge (IC chip, barcode, photo,  │
│      damped pendulum physics swing & holographic glare sweep)          │
│    - Right: Telemetry & KPI dashboard (3 metric tiles, animated        │
│      repository footprint bar charts & radar pulse indicator)          │
├────────────────────────────────────────────────────────────────────────┤
│ 5. FEATURED ENGINEERING & BUILDS (Markdown Table)                      │
│    - Flagship repos, autonomous AI systems, and educational courses    │
├────────────────────────────────────────────────────────────────────────┤
│ 6. DUAL CONTRIBUTION CITY & SNAKE (profile-3d.yml + snake.yml)         │
│    - "🌃 My Contribution City" tagline                                 │
│    - 3D Isometric Night Skyline City (yoshi389111/github-profile-3d)   │
│    - Contribution Snake eating commit dots (Platane/snk via <picture>) │
├────────────────────────────────────────────────────────────────────────┤
│ 7. INTERACTIVE CONNECT CARD & METRICS (connect.svg)                    │
│    - Ambient glowing orbs, pulsing collaboration tracks & arrows       │
│    - Direct clickable shields.io badges (LinkedIn, Email, GitHub)      │
│    - Live profile views counter badge (komarev.com/ghpvc)              │
└────────────────────────────────────────────────────────────────────────┘
```

---

## Step-by-Step Implementation Workflow

### Step 1: Character Art & Avatar Cutout Generation

Prompt any AI image generator (Midjourney, DALL-E, Gemini) to generate an anime-style character illustration with a pure white or transparent background for a clean cutout.

#### Master Character Prompt:
```text
High-quality anime-style digital illustration of a young software developer, relaxed in a sleek modern ergonomic chair with a dark laptop on lap, softly smiling. Wearing a cozy dark zip-up hoodie over a tech t-shirt, jeans, sunglasses resting on head. Beside them on a small glass-top table: a stack of programming books reading "Python", "Agentic AI", "Docker", "System Architecture", a takeaway coffee cup with "Code. Coffee. Repeat." written on it, and a small potted desk plant. Pure white background, warm soft rim lighting, clean detailed anime art style, vibrant colors, high resolution, full body in frame.
```

#### Avatar Optimization for SVG Embedding:
1. Crop the avatar into a circular photo (at least 300x300px).
2. Save as **PNG** or **JPEG** (never WebP — Safari fails to decode WebP inside standalone SVGs).
3. Convert to Base64 data URI using terminal:
   ```bash
   base64 -i avatar.png | pbcopy   # On macOS
   ```
4. Embed into the SVG inside an `<image>` element:
   ```xml
   <image href="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAA..."
          x="158" y="218" width="104" height="104"
          clip-path="url(#dash-photoclip)" preserveAspectRatio="xMidYMid slice" />
   ```

---

### Step 2: Generate Core Animated SVGs

All SVGs must use `width="100%"` and `height="auto"` with fixed `viewBox` coordinates to achieve responsive scaling on all display widths.

---

#### Card 1: Camera Viewfinder Hero & Walking Mascot (`hero.svg`)
* **Dimensions**: `viewBox="0 0 1280 580"`.
* **Visual Components**:
  * **Viewfinder HUD Framing**: Outer glow border (`stroke="url(#h-border)"`), corner brackets (`.hud-corner`), dot grid background.
  * **Status & Timecode**: Blinking red REC dot (`@keyframes recBlink`), timecode counter (`00:14:32:08`), resolution tags (`4K 60FPS HDR`).
  * **Audio Equalizer**: 3 vertical bars animating on staggered loops (`eq-1`, `eq-2`, `eq-3`).
  * **Scrubber Playhead**: Playhead moving horizontally across the bottom timeline (`@keyframes scrubPlay`).
  * **Shimmer Name**: Multi-stop gradient cycling through `#22d3ee`, `#c084fc`, `#ef4444`, `#34d399` on a 6s loop.
  * **Cycling Role Headlines**: 3 stacked headlines rotated every 3 seconds (9s full cycle) using `@keyframes role1`, `role2`, `role3`.
  * **Walking Vector Mascot**:
    * Walking cycle root translation (`mascotWalkPos`).
    * Torso bobbing (`mascotBob`).
    * Hip-hinged leg swing (`legLeft`, `legRight`).
    * Arm swing and martial arts salute/wave (`armLeftSwing`, `armRightSwing`).
    * Responsive floor shadow scaling (`shadowScale`).

##### Key CSS Snippet (`hero.svg`):
```css
/* REC Blinking Dot */
@keyframes recBlink { 0%, 100% { opacity: 1; transform: scale(1); } 50% { opacity: 0.15; transform: scale(0.85); } }
.rec-dot { animation: recBlink 1.2s infinite ease-in-out; transform-origin: 30px 24px; }

/* Scrubber Timeline Playhead */
@keyframes scrubPlay { 0% { transform: translateX(0px); } 100% { transform: translateX(450px); } }
.scrubber-head { animation: scrubPlay 4s linear infinite; }

/* Role Switcher (9s Loop: 3 Roles x 3s) */
@keyframes role1 { 0%, 28% { opacity: 1; transform: translateY(0); } 33.3%, 100% { opacity: 0; transform: translateY(-16px); } }
@keyframes role2 { 0%, 30% { opacity: 0; transform: translateY(16px); } 33.3%, 61% { opacity: 1; transform: translateY(0); } 66.6%, 100% { opacity: 0; transform: translateY(-16px); } }
@keyframes role3 { 0%, 63% { opacity: 0; transform: translateY(16px); } 66.6%, 95% { opacity: 1; transform: translateY(0); } 100% { opacity: 0; transform: translateY(-16px); } }
.role-text-1 { animation: role1 9s infinite; }
.role-text-2 { animation: role2 9s infinite; }
.role-text-3 { animation: role3 9s infinite; }

/* Mascot Walk & Salute Cycle */
@keyframes mascotWalkPos { 0% { transform: translateX(170px); } 50% { transform: translateX(180px); } 100% { transform: translateX(170px); } }
@keyframes mascotBob { 0%, 100% { transform: translateY(0px); } 20%, 40% { transform: translateY(-7px); } 50%, 70% { transform: translateY(-2px); } }
@keyframes legLeft { 0%, 100% { transform: rotate(18deg); } 20% { transform: rotate(-22deg); } 40%, 75% { transform: rotate(0deg); } 95% { transform: rotate(-22deg); } }
@keyframes legRight { 0%, 100% { transform: rotate(-22deg); } 20% { transform: rotate(18deg); } 40%, 75% { transform: rotate(0deg); } 95% { transform: rotate(18deg); } }
@keyframes armLeftSwing { 0%, 100% { transform: rotate(-20deg); } 20% { transform: rotate(25deg); } 50%, 70% { transform: rotate(-65deg); } }
@keyframes armRightSwing { 0%, 100% { transform: rotate(25deg); } 20% { transform: rotate(-20deg); } 50%, 70% { transform: rotate(35deg); } }
```

---

#### Card 2: What I Build & Life Beyond Code (`about-life.svg`)
* **Dimensions**: `viewBox="0 0 1280 640"`.
* **Visual Components**:
  * **Dual Card Grid**: Two equal-width glassmorphic panels (`620px` each) separated by a `40px` gutter.
  * **Left Panel ("What I Build")**:
    * Browser window frame with macOS red/yellow/green control dots.
    * URL bar pill: `🔒 shivam.dev/agentic-platform` with blinking cursor.
    * 3 capability rows: Agentic AI Test Synthesis, Resilient Platform Engineering, and Backend Microservices.
  * **Right Panel ("Life Beyond The Terminal")**:
    * Instagram / Stories header with live pulsing status indicator.
    * **Automated 3-Slide Carousel**: MMA / Combat Sports (Slide 1), Psychology & Human Behavior (Slide 2), Wilderness Travel & Exploration (Slide 3).
    * **Top Segment Progress Bars**: 3 horizontal timer bars filling progressively (`alBar1`, `alBar2`, `alBar3`) over 12 seconds (`width: 0` to `width: 170px`).
    * **Activity Rings**: Circular SVG progress rings animating via `stroke-dashoffset` (`ringCombat`).

##### Key CSS Snippet (`about-life.svg`):
```css
/* 12s Story Carousel (3 Slides x 4s) */
@keyframes alSlide1 { 0%, 30% { opacity: 1; transform: translateX(0); } 33.3%, 96.6% { opacity: 0; transform: translateX(24px); } 100% { opacity: 1; transform: translateX(0); } }
@keyframes alSlide2 { 0%, 30% { opacity: 0; transform: translateX(-24px); } 33.3%, 63.3% { opacity: 1; transform: translateX(0); } 66.6%, 100% { opacity: 0; transform: translateX(24px); } }
@keyframes alSlide3 { 0%, 63.3% { opacity: 0; transform: translateX(-24px); } 66.6%, 96.6% { opacity: 1; transform: translateX(0); } 100% { opacity: 0; transform: translateX(-24px); } }
.al-slide-1 { animation: alSlide1 12s cubic-bezier(0.2, 0.8, 0.2, 1) infinite; }
.al-slide-2 { animation: alSlide2 12s cubic-bezier(0.2, 0.8, 0.2, 1) infinite; }
.al-slide-3 { animation: alSlide3 12s cubic-bezier(0.2, 0.8, 0.2, 1) infinite; }

/* Story Timer Bars */
@keyframes alBar1 { 0% { width: 0px; } 28%, 100% { width: 170px; } }
@keyframes alBar2 { 0%, 33.3% { width: 0px; } 61%, 100% { width: 170px; } }
@keyframes alBar3 { 0%, 66.6% { width: 0px; } 95%, 100% { width: 170px; } }
.al-prog-1 { animation: alBar1 12s linear infinite; }
.al-prog-2 { animation: alBar2 12s linear infinite; }
.al-prog-3 { animation: alBar3 12s linear infinite; }

/* Activity Rings */
@keyframes ringCombat { 0% { stroke-dashoffset: 150; } 50% { stroke-dashoffset: 15; } 100% { stroke-dashoffset: 150; } }
.ring-mma { stroke-dasharray: 150; animation: ringCombat 6s ease-in-out infinite; }
.ring-psy { stroke-dasharray: 150; animation: ringCombat 6s ease-in-out infinite 0.8s; }
.ring-trv { stroke-dasharray: 150; animation: ringCombat 6s ease-in-out infinite 1.6s; }
```

---

#### Card 3: Tech Orbit & Capability System (`stack.svg`)
* **Dimensions**: `viewBox="0 0 1280 500"` (or `viewBox="0 0 680 380"` for compact view).
* **Visual Components**:
  * **Glowing Central Core**: Representing primary domain (e.g. `AGENTIC AI & QA PLATFORMS`).
  * **3 Concentric Elliptical Orbits**: Inner orbit (`18s`), Middle orbit (`26s`), Outer orbit (`36s`) with dashed orbital paths.
  * **Planetary Satellites**: Tech icons revolving around the center (Python, Docker, TypeScript, Playwright, CI/CD, Kubernetes).
  * **Right-Side Architectural Pillars**: Capability metrics (e.g. Test Coverage: 95%+, Execution Speed: 3x, MTTR: <10m).

---

#### Card 4: Developer ID & Live Telemetry Dashboard (`id-dashboard.svg`)
* **Dimensions**: `viewBox="0 0 1280 620"`.
* **Visual Components**:
  * **Left Zone (Swinging Lanyard Pass)**:
    * Woven fabric strap entering from above the canvas.
    * Metallic clasp, swivel ring, badge slot.
    * Realistic glassmorphic badge with golden smart chip IC.
    * Circular photo ring with Base64 developer portrait.
    * Developer metadata (Name, Title, Clearance, Location).
    * Vector barcode with unique serial tag (`SN-007-PASS`).
    * Damped pendulum swing physics (`dropIn` + `swayForever`).
    * Holographic glare bar sweeping diagonally every 5.5s (`dash-foil`).
  * **Right Zone (Live Telemetry & Metrics Dashboard)**:
    * Title: `// TELEMETRY & METRICS — Engineering Impact & Focus`.
    * **3 Top KPI Metric Tiles**:
      1. Experience (`~7.5+ Years`, QA & Platform Systems).
      2. Quality Standard (`100% Automation`, Zero Flaky Gates).
      3. Community (`500+ Mentored`, Python & DevOps Training).
    * **Primary Repository Footprint**: Horizontal bar charts with smooth grow animations (`barGrow1`, `barGrow2`, `barGrow3`).
    * **Radar Indicator**: Pulsing radar ring (`@keyframes radarPulse`).

##### Key CSS Snippet (`id-dashboard.svg`):
```css
/* Pendulum Physics Swing */
@keyframes dropIn {
  0% { transform: translateY(-500px) rotate(0deg); }
  22% { transform: translateY(0) rotate(0deg); }
  42% { transform: rotate(4deg); }
  62% { transform: rotate(-2.5deg); }
  80% { transform: rotate(1.4deg); }
  92% { transform: rotate(-0.6deg); }
  100% { transform: rotate(0deg); }
}
@keyframes swayForever {
  0%, 100% { transform: rotate(-1.5deg); }
  50% { transform: rotate(1.5deg); }
}
.dash-swing {
  transform-origin: 210px 0px;
  animation: dropIn 2.6s cubic-bezier(0.3, 1, 0.5, 1) forwards, swayForever 6s ease-in-out 2.6s infinite;
}

/* Diagonal Holographic Glare */
@keyframes foilSweep { 0% { transform: translateX(-350px); } 55%, 100% { transform: translateX(380px); } }
.dash-foil { animation: foilSweep 5.5s ease-in-out infinite; }

/* KPI Horizontal Bar Growth */
@keyframes barGrow1 { from { width: 0px; } to { width: 520px; } }
@keyframes barGrow2 { from { width: 0px; } to { width: 440px; } }
@keyframes barGrow3 { from { width: 0px; } to { width: 380px; } }
.bar-1 { animation: barGrow1 1.2s cubic-bezier(0.2, 0.8, 0.2, 1) both 0.4s; }
.bar-2 { animation: barGrow2 1.2s cubic-bezier(0.2, 0.8, 0.2, 1) both 0.6s; }
.bar-3 { animation: barGrow3 1.2s cubic-bezier(0.2, 0.8, 0.2, 1) both 0.8s; }
```

---

#### Card 5: Interactive Connect & Collaborate Footer (`connect.svg`)
* **Dimensions**: `viewBox="0 0 1280 480"`.
* **Visual Components**:
  * **Left Column**: Headline ("Let's build something autonomous & exceptional"), collaboration scopes, and status pill (`PUNE, INDIA • AVAILABLE REMOTELY`).
  * **Right Column**: 4 branded interactive cards (LinkedIn, GitHub, Email, Calendly/X) with subtle border pulsing (`card-pulse-1..4`) and animated nudging arrows (`@keyframes arrowNudge`).
  * **Ambient Lighting**: Colored radial gradient orbs with Gaussian blur filters drifting subtly in the background (`@keyframes floatOrb`).

##### Key CSS Snippet (`connect.svg`):
```css
/* Animated Nudging Arrows */
@keyframes arrowNudge { 0%, 100% { transform: translateX(0); } 50% { transform: translateX(6px); } }
.arrow-nudge { animation: arrowNudge 1.6s ease-in-out infinite; }

/* Staggered Card Glow Pulse */
@keyframes cardPulse { 0%, 100% { stroke-opacity: 0.2; } 50% { stroke-opacity: 0.8; } }
.card-pulse-1 { animation: cardPulse 3s ease-in-out infinite; }
.card-pulse-2 { animation: cardPulse 3s ease-in-out infinite 0.75s; }
.card-pulse-3 { animation: cardPulse 3s ease-in-out infinite 1.5s; }
.card-pulse-4 { animation: cardPulse 3s ease-in-out infinite 2.25s; }
```

---

### Step 3: Setup Dual Contribution Visualizer Workflows

Instead of choosing one, top profiles combine **both** the 3D Skyline City and the Contribution Snake sequentially.

#### 1. Contribution Snake Workflow (`.github/workflows/snake.yml`)
Runs daily at midnight UTC, pulls contribution data, generates light and dark SVGs, and publishes them to the `output` orphan branch:

```yaml
name: Generate Snake Contribution Animation

on:
  schedule:
    - cron: "0 0 * * *"
  workflow_dispatch:
  push:
    branches:
      - main

permissions:
  contents: write

jobs:
  generate:
    runs-on: ubuntu-latest
    timeout-minutes: 5

    steps:
      - name: Generate snake.svg
        uses: Platane/snk/svg-only@v3
        with:
          github_user_name: ${{ github.repository_owner }}
          outputs: |
            dist/github-contribution-grid-snake.svg
            dist/github-contribution-grid-snake-dark.svg?palette=github-dark&color_snake=#38bdf8&color_dots=#161b22,#0e4429,#006d32,#26a641,#39d353
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}

      - name: Push snake animation to output branch
        uses: crazy-max/ghaction-github-pages@v3.1.0
        with:
          target_branch: output
          build_dir: dist
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
```

#### 2. 3D Contribution Skyline Workflow (`.github/workflows/profile-3d.yml`)
Renders the contribution skyline city into `profile-3d-contrib/profile-night-view.svg` directly in the main branch:

```yaml
name: GitHub 3D Contribution Calendar

on:
  schedule:
    - cron: "0 18 * * *"
  workflow_dispatch:

permissions:
  contents: write

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: yoshi389111/github-profile-3d-contrib@0.7.2
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
          USERNAME: ${{ github.repository_owner }}
      - name: Commit & Push 3D Assets
        run: |
          git config user.name github-actions
          git config user.email github-actions@github.com
          git add -A .
          git commit -m "chore: regenerate 3D profile calendar skyline" || exit 0
          git push
```

> [!IMPORTANT]
> In repository settings under **Settings > Actions > General > Workflow permissions**, ensure **"Read and write permissions"** is selected.

---

### Step 4: Assembling the Production `README.md`

Use the exact layout structure proven on `shivamnamdev/shivamnamdev`:

```markdown
<div align="center">

  <!-- ================= 1. HERO VIEWFINDER & WALKING AVATAR ================= -->
  <img src="hero.svg?v=1" width="100%" alt="Developer Name — Role Title | Camera Viewfinder Hero">

  <br/><br/>

  <!-- ================= 2. WHAT I BUILD & LIFE BEYOND CODE ================= -->
  <img src="about-life.svg?v=1" width="100%" alt="What I build, and life beyond the terminal" />

  <br/><br/>

  <!-- ================= 3. CAPABILITIES & TECH ORBIT ================= -->
  <img src="stack.svg?v=1" width="100%" alt="Tech Orbit & Architectural Pillars" />

  <br/><br/>

  <!-- ================= 4. DEVELOPER ID & TELEMETRY DASHBOARD ================= -->
  <img src="id-dashboard.svg?v=1" width="100%" alt="Developer ID and Live Telemetry Dashboard" />

  <br/><br/>

</div>

## 🚀 Featured Engineering & Builds

| Project / Curriculum | Core Capability & Architecture | Tech Stack | Link |
| :--- | :--- | :--- | :---: |
| [**MyAITesterBlueprint**](https://github.com/USER/MyAITesterBlueprint) | Autonomous Agentic AI system for automated test scenario synthesis, DOM discovery, and quality validation. | `Python` `Agentic AI` `Playwright` `LLMs` | [**Explore Repo →**](https://github.com/USER/MyAITesterBlueprint) |
| [**learn-python-step-by-step**](https://github.com/USER/learn-python-step-by-step) | Practical, zero-fluff modular guide to mastering modern Python from fundamentals to production scripting. | `Python 3.12` `Automation` `Algorithms` | [**Explore Repo →**](https://github.com/USER/learn-python-step-by-step) |

<br/>

<div align="center">

  <!-- ================= 5. 3D CONTRIBUTION CITY & SNAKE ================= -->
  <h2>🌃 My Contribution City</h2>
  <p><em>Every commit builds another skyscraper — rebuilt automatically every day.</em></p>

  <img src="profile-3d-contrib/profile-night-view.svg" width="100%" alt="3D Contribution Skyline" onerror="this.style.display='none'" />

  <br/><br/>

  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/USER/USER/output/github-contribution-grid-snake-dark.svg">
    <source media="(prefers-color-scheme: light)" srcset="https://raw.githubusercontent.com/USER/USER/output/github-contribution-grid-snake.svg">
    <img src="https://raw.githubusercontent.com/USER/USER/output/github-contribution-grid-snake.svg" alt="GitHub Contribution Snake" width="100%">
  </picture>

  <br/><br/>

  <!-- ================= 6. INTERACTIVE CONNECT FOOTER ================= -->
  <img src="connect.svg?v=1" width="100%" alt="Let's Connect and Collaborate" />

  <br/><br/>

  <!-- Direct Clickable Social Badges -->
  <p align="center">
    <a href="https://www.linkedin.com/in/USER/" target="_blank">
      <img src="https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn" />
    </a>
    &nbsp;&nbsp;
    <a href="mailto:user@example.com">
      <img src="https://img.shields.io/badge/Email-EA4335?style=for-the-badge&logo=gmail&logoColor=white" alt="Email" />
    </a>
    &nbsp;&nbsp;
    <a href="https://github.com/USER">
      <img src="https://img.shields.io/badge/GitHub-181717?style=for-the-badge&logo=github&logoColor=white" alt="GitHub" />
    </a>
  </p>

  <br/>

  <!-- Profile Views Counter Badge -->
  <img src="https://komarev.com/ghpvc/?username=USER&color=22d3ee&style=for-the-badge&label=PROFILE+VIEWS" alt="Profile views counter" />

  <br/><br/>

  <p><strong>Always learning, always building. ⚡</strong></p>

</div>
```

---

## Critical Rules & Technical Gotchas

### 1. The GitHub Camo CDN Cache-Busting Rule (`?v=1` ➔ `?v=2`)
* GitHub routes all images through its Camo proxy CDN (`camo.githubusercontent.com`) and caches them aggressively.
* **Problem**: When you update an SVG file and push to GitHub, the profile continues to display the old cached version.
* **Solution**: Always append a query version parameter in `README.md` (`hero.svg?v=1`). Whenever you edit an SVG, increment the version query (`hero.svg?v=2`).
* **Commit Order of Operations**:
  1. Commit and push the updated SVG files first.
  2. Commit and push the `README.md` with the incremented version number second.

### 2. Base64 Image Encoding (PNG & JPEG over WebP)
* When embedding portraits or textures via `<image href="data:image/png;base64,..." />`, use **PNG** or **JPEG**.
* Safari (iOS and macOS) fails to decode Base64 WebP inside standalone SVG files.

### 3. XML Entity Escaping
* Standalone SVGs are parsed strictly as XML.
* **Strictly Forbidden**: Unescaped ampersands (`&`), less-thans (`<`), or greater-thans (`>`) anywhere—including inside CSS `@keyframes` and `<text>` elements.
* Always escape them:
  * Replace `&` with `&amp;` (e.g. `QA &amp; Platform Architect`)
  * Replace `<` with `&lt;`
  * Replace `>` with `&gt;`

### 4. Text Reveal Window Padding (No Font Clipping)
* Different operating systems (macOS, Windows, Linux) calculate font metrics and ascender/descender bounds differently.
* When using `<clipPath>` for typing reveals or card windows, add at least **10–14px padding** above and below the text bounding box to prevent clipping letters like `g`, `y`, `p`, `j`, and `Q`.

### 5. Fallback States for Animation-Disabled Environments
* Accessibility modes (e.g., `prefers-reduced-motion`) or static image proxies may disable CSS animations.
* Always specify `animation-fill-mode: both` on animated elements and define valid initial coordinates and opacities so the SVG displays complete, readable information even if animations do not run.

### 6. Unique ID Namespacing Per SVG
* If two SVG files rendered on the same page share identical element IDs (e.g., `<linearGradient id="card-bg">`), browsers may apply the gradient from the first SVG to the second SVG.
* Namespace all IDs with a unique file prefix:
  * In `hero.svg`: `h-bg`, `h-border`, `name-shimmer`, `cam-clip`.
  * In `about-life.svg`: `al-cardbg`, `al-edgeL`, `al-browser-clip`.
  * In `id-dashboard.svg`: `dash-bg`, `dash-idclip`, `dash-foil`.
  * In `connect.svg`: `conn-bg`, `conn-edge`, `conn-glow`.

---

## Production Release Checklist

- [ ] Profile repository created with exact username match (`username/username`).
- [ ] AI character portrait generated with clean cutout and converted to Base64 (PNG/JPEG).
- [ ] `hero.svg`, `about-life.svg`, `stack.svg`, `id-dashboard.svg`, and `connect.svg` created and tested in browser.
- [ ] All SVGs validated through an XML parser with 0 errors (escaped `&amp;`, `&lt;`, `&gt;`).
- [ ] All SVG IDs namespaced with file-specific prefixes to prevent cross-contamination.
- [ ] GitHub Actions workflow permission set to **Read and write permissions** in repository settings.
- [ ] `snake.yml` executed and verified on the `output` branch.
- [ ] `profile-3d.yml` executed and verified in `profile-3d-contrib/`.
- [ ] Cache-busting version query (`?v=1`) verified on all image URLs in `README.md`.
- [ ] Social badges, repository links, and email mailto links tested with active URLs.
