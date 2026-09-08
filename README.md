# SlideForge

## PPTX Viewer & Editor

SlideForge is a web-based PowerPoint presentation viewer and editor designed to read, render, edit, and export `.pptx` files directly through a modern web interface.

The project is being developed as a two-member team with a modular architecture that separates PPTX processing, rendering, editing, shared data, and presentation export.

---

## 🚀 Project Overview

PowerPoint files (`.pptx`) contain structured XML, relationships, media, themes, layouts, and other presentation resources.

SlideForge aims to provide a complete workflow:

```text
PPTX File
    ↓
Read & Extract
    ↓
Parse Presentation Data
    ↓
Shared Data Model
    ↓
Render Slides
    ↓
View & Edit
    ↓
Update Presentation Data
    ↓
Export
    ↓
New PPTX File
```

The architecture is designed to be modular so that the PPTX engine and frontend editor can be developed independently and connected through a shared data model.

---

## 🎯 Project Objectives

* Read and process `.pptx` files.
* Parse slides and presentation elements.
* Extract text, shapes, images, and geometry.
* Convert PowerPoint data into a common internal model.
* Render slides in a web browser.
* Provide interactive editing capabilities.
* Support selection, dragging, resizing, and rotation.
* Support text editing.
* Export edited presentations back to `.pptx`.
* Maintain a clean and scalable project architecture.
* Provide automated tests for core functionality.

---

## ✨ Planned Features

### PPTX Processing

* PPTX file reading
* ZIP/XML processing
* Slide parsing
* Shape parsing
* Text extraction
* Image extraction
* Presentation models
* Geometry and transformations

### Slide Viewer

* Slide rendering
* Multiple slide navigation
* Slide canvas
* Zoom and viewing support
* Image and shape rendering
* Text rendering

### Slide Editor

* Element selection
* Drag and drop
* Resize elements
* Rotate elements
* Text editing
* Properties panel
* Interactive editing

### PPTX Export

* Presentation serialization
* Slide serialization
* XML generation
* Export edited presentation as `.pptx`

---

# 🏗️ Project Architecture

SlideForge follows a modular monorepo architecture.

```text
SlideForge
│
├── Core
│   └── Reads and parses PPTX files
│
├── Shared
│   └── Common presentation data model
│
├── Renderer
│   └── Converts presentation data into visual slides
│
├── Editor
│   └── Handles user interaction and editing
│
├── Exporter
│   └── Converts edited data back into PPTX
│
└── Web App
    └── Provides the user interface
```

---

# 📁 Project Structure

```text
slideforge/
│
├── packages/
│   │
│   ├── core/
│   │   ├── src/
│   │   │   ├── parser/
│   │   │   ├── models/
│   │   │   ├── geometry/
│   │   │   └── index.ts
│   │   └── package.json
│   │
│   ├── renderer/
│   │   ├── src/
│   │   │   ├── slide-renderer.ts
│   │   │   ├── shape-renderer.ts
│   │   │   ├── text-renderer.ts
│   │   │   ├── image-renderer.ts
│   │   │   └── index.ts
│   │   └── package.json
│   │
│   ├── editor/
│   │   ├── src/
│   │   │   ├── selection.ts
│   │   │   ├── drag.ts
│   │   │   ├── resize.ts
│   │   │   ├── rotate.ts
│   │   │   ├── text-editor.ts
│   │   │   └── index.ts
│   │   └── package.json
│   │
│   ├── shared/
│   │   ├── src/
│   │   │   ├── types.ts
│   │   │   ├── constants.ts
│   │   │   └── index.ts
│   │   └── package.json
│   │
│   └── exporter/
│       ├── src/
│       │   ├── pptx-writer.ts
│       │   ├── slide-writer.ts
│       │   ├── xml-builder.ts
│       │   └── index.ts
│       └── package.json
│
├── apps/
│   └── web/
│       ├── src/
│       │   ├── components/
│       │   ├── pages/
│       │   ├── hooks/
│       │   ├── store/
│       │   ├── styles/
│       │   └── main.tsx
│       └── public/
│
├── tests/
│   ├── parser/
│   ├── renderer/
│   ├── editor/
│   └── exporter/
│
├── docs/
│   ├── architecture.md
│   ├── development.md
│   └── SlideForge_README.docx
│
├── examples/
├── scripts/
│
├── .gitignore
├── package.json
├── tsconfig.json
└── README.md
```

---

# 👥 Team Structure

SlideForge is developed by a two-member team.

## Member 1 — Shreya Tiwari

### Role: Core PPTX Engine & Export

Responsibilities:

```text
packages/core/
packages/exporter/
tests/parser/
tests/exporter/
```

Main workflow:

```text
PPTX
  ↓
Read ZIP
  ↓
Read XML
  ↓
Parse Slides
  ↓
Parse Shapes & Text
  ↓
Create Presentation Data
  ↓
Export Updated Data
  ↓
PPTX
```

### Main Tasks

* PPTX file reading
* XML parsing
* Slide parsing
* Shape parsing
* Text parsing
* Image handling
* Geometry processing
* Presentation models
* PPTX serialization
* Export testing

---

# Member 2 — Sadhna Pandey

### Role: Frontend Viewer, Editor & Interaction

Responsibilities:

```text
packages/shared/
packages/renderer/
packages/editor/
apps/web/
tests/renderer/
tests/editor/
```

Main workflow:

```text
Presentation Data
       ↓
Shared Model
       ↓
Renderer
       ↓
Web Interface
       ↓
Select Element
       ↓
Drag / Resize / Rotate
       ↓
Edit Content
       ↓
Updated Presentation Data
```

### Main Tasks

* Shared data model integration
* Slide rendering
* Web UI
* Slide canvas
* Slide navigation
* Element selection
* Dragging
* Resizing
* Rotation
* Text editing
* Properties panel
* Frontend testing

---

# 🔗 Integration Between Team Members

The `shared` package acts as the bridge between the PPTX engine and the frontend.

```text
             SHREYA
        PPTX Core / Parser
                │
                ▼
       Presentation Data
                │
                ▼
          packages/shared
                │
                ▼
             SADHNA
       Renderer / Editor
                │
                ▼
        Updated Slide Data
                │
                ▼
          PPTX Exporter
                │
                ▼
          Final .pptx
```

This separation allows both team members to work independently while maintaining a common data contract.

---

# 🛠️ Technology Stack

| Technology        | Purpose                         |
| ----------------- | ------------------------------- |
| TypeScript        | Main programming language       |
| React             | Web application UI              |
| Node.js           | Development/runtime environment |
| XML               | PowerPoint presentation data    |
| PPTX/Open XML     | Presentation file format        |
| Git               | Version control                 |
| GitHub            | Source code collaboration       |
| Testing Framework | Automated testing               |

---

# 🔄 Development Workflow

The project will be developed in multiple phases.

## Phase 1 — Project Setup

* Repository setup
* Monorepo structure
* TypeScript configuration
* Package configuration
* Git workflow

## Phase 2 — PPTX Parser

* Read `.pptx`
* Extract XML
* Parse presentation
* Parse slides
* Parse shapes
* Parse text
* Parse images

## Phase 3 — Shared Data Model

* Define presentation types
* Define slide types
* Define element types
* Define geometry
* Connect parser with shared model

## Phase 4 — Viewer

* Create web application
* Render slides
* Display text
* Display shapes
* Display images
* Add slide navigation

## Phase 5 — Editor

* Selection
* Drag
* Resize
* Rotate
* Text editing
* Properties panel

## Phase 6 — Export

* Convert edited data to XML
* Generate PPTX structure
* Create downloadable `.pptx`

## Phase 7 — Testing

* Parser tests
* Renderer tests
* Editor tests
* Exporter tests
* End-to-end testing

---

# 🌿 Git & GitHub Workflow

The project uses feature branches to avoid directly modifying the `main` branch.

```text
main
 │
 ├── feature/core-parser
 │       └── Shreya
 │
 └── feature/frontend-editor
         └── Sadhna
```

### Create a feature branch

```bash
git checkout -b feature/your-feature
```

### Check changes

```bash
git status
```

### Add changes

```bash
git add .
```

### Commit

```bash
git commit -m "Describe your changes"
```

### Push branch

```bash
git push -u origin feature/your-feature
```

### Pull Request

After completing a feature, create a Pull Request from the feature branch to `main`.

---

# 🚀 Getting Started

Clone the repository:

```bash
git clone https://github.com/pandeysadhna537-hub/IBM_project.git
```

Move into the project:

```bash
cd IBM_project
```

Install dependencies:

```bash
npm install
```

Start the development environment:

```bash
npm run dev
```

---

# 🧪 Testing

Tests are organized according to the project modules.

```text
tests/
├── parser/
├── renderer/
├── editor/
└── exporter/
```

Run the project's test command after the testing configuration is completed:

```bash
npm test
```

---

# 📌 Current Project Status

### Completed

* Project structure created
* Monorepo directories created
* Core package structure created
* Renderer package structure created
* Editor package structure created
* Shared package structure created
* Exporter package structure created
* Web application structure created
* Test directories created
* Git repository initialized
* GitHub repository connected

### In Progress

* PPTX parser implementation
* Shared presentation data model
* Slide renderer
* Editor interactions
* PPTX exporter

---

# 🔮 Future Scope

Future versions of SlideForge may include:

* Advanced PowerPoint compatibility
* Master slide support
* Themes and layouts
* Animations and transitions
* Charts and tables
* Advanced typography
* SVG and vector graphics
* Collaboration features
* Cloud storage
* AI-assisted slide editing
* AI content generation
* Presentation templates
* Real-time collaborative editing

---

# 📄 Documentation

Additional project documentation is available in:

```text
docs/
├── architecture.md
├── development.md
└── SlideForge_README.docx
```

---

# 🤝 Team

### Shreya Tiwari

**Core PPTX Engine & Export**

### Sadhna Pandey

**Frontend Viewer, Editor & Interaction**

---

# 📜 License

This project is developed for educational and project development purposes.
