# GitHub Pages HTML Sharing Guide

## How to Share HTML Files from Your Local Projects

This guide explains how to transfer HTML files from your local R projects (like DDUH_DS) to your GitHub Pages repository for external sharing.

---

## 📁 Repository Structure

Your `oral-health-nutrition.github.io` repository should be organized like this:

```
oral-health-nutrition.github.io/
├── COP_nutrition_survey/
│   ├── index.html
│   ├── IADR_25_FINAL_8.html
│   ├── regional_sand_global_survey_analysis_V19.html
│   └── regional_survey_analysis_12.html
├── fluoride_research/
│   ├── index.html
│   └── [fluoride HTML files]
├── datasets/
│   └── [CSV files if needed]
└── README.md
```

---

## 🔄 Step-by-Step Process

### Step 1: Generate HTML from R Markdown

In your local R project (e.g., DDUH_DS):

```r
# In RStudio, render your .Rmd file to HTML
rmarkdown::render("your_analysis.Rmd", output_format = "html_document")

# Or use the Knit button in RStudio
```

### Step 2: Locate Your HTML Files

Your HTML files will be in your local project directory:
```
~/Documents/DDUH_DS/
├── dental_survey_analysis.html
├── regional_analysis.html
└── IADR_presentation.html
```

### Step 3: Copy Files to GitHub Repository

#### Option A: Using Finder/File Explorer
1. **Navigate** to your local GitHub repository:
   ```
   ~/Documents/oral-health-nutrition.github.io/COP_nutrition_survey/
   ```
2. **Copy** HTML files from your DDUH_DS project to the appropriate folder
3. **Rename** files if needed (e.g., `analysis.html` → `survey_analysis_v19.html`)

#### Option B: Using Terminal/Command Line
```bash
# Navigate to your GitHub repository
cd ~/Documents/oral-health-nutrition.github.io/COP_nutrition_survey/

# Copy HTML files from your R project
cp ~/Documents/DDUH_DS/dental_survey_analysis.html ./regional_sand_global_survey_analysis_V19.html
cp ~/Documents/DDUH_DS/IADR_slides.html ./IADR_25_FINAL_8.html

# List files to confirm
ls -la *.html
```

### Step 4: Add and Commit to Git

```bash
# Navigate to repository root
cd ~/Documents/oral-health-nutrition.github.io/

# Check status
git status

# Add new/updated files
git add COP_nutrition_survey/*.html

# Commit with descriptive message
git commit -m "Add updated survey analysis HTML files with real data"

# Push to GitHub
git push origin main
```

### Step 5: Verify Online

Check that your files are live:
- **Direct file**: `https://oral-health-nutrition.github.io/COP_nutrition_survey/IADR_25_FINAL_8.html`
- **Index page**: `https://oral-health-nutrition.github.io/COP_nutrition_survey/`

---

## 🔗 Sharing URLs

### Individual Files
```
https://oral-health-nutrition.github.io/COP_nutrition_survey/IADR_25_FINAL_8.html
https://oral-health-nutrition.github.io/COP_nutrition_survey/regional_sand_global_survey_analysis_V19.html
```

### Index Pages
```
https://oral-health-nutrition.github.io/COP_nutrition_survey/
https://oral-health-nutrition.github.io/fluoride_research/
```

### Main Repository
```
https://oral-health-nutrition.github.io/
```

---

## 📝 Best Practices

### File Naming
- **Use descriptive names**: `survey_analysis_v19.html` not `analysis.html`
- **Include version numbers**: `_v19`, `_final`, `_2025` for clarity
- **No spaces**: Use underscores or hyphens instead

### Organization
- **Group by project**: COP survey, fluoride research, etc.
- **Create index pages**: For each project folder
- **Update regularly**: Keep HTML files current with R analysis

### Git Workflow
```bash
# Daily workflow
git pull origin main          # Get latest changes
# ... copy new HTML files ...
git add .                     # Stage all changes
git commit -m "Update analysis with latest data"
git push origin main          # Push to GitHub
```

---

## 🛠 Automation Tips

### R Script for Batch Export
Create an R script to render multiple files:

```r
# render_all.R
files_to_render <- c(
  "survey_analysis.Rmd",
  "regional_analysis.Rmd", 
  "IADR_presentation.Rmd"
)

for(file in files_to_render) {
  rmarkdown::render(file, output_format = "html_document")
}

# Copy to GitHub repository
file.copy("survey_analysis.html", 
          "~/Documents/oral-health-nutrition.github.io/COP_nutrition_survey/survey_analysis_v19.html",
          overwrite = TRUE)
```

### Git Aliases (Optional)
Add to your `~/.gitconfig`:

```ini
[alias]
    webpage = !git add . && git commit -m "Update web content" && git push origin main
```

Then use: `git webpage`

---

## 🔧 Troubleshooting

### Common Issues

**Files not showing online**
- Check GitHub Pages is enabled in repository settings
- Ensure files are in correct folder structure
- Verify git push completed successfully

**Broken links in HTML**
- Use relative paths in R Markdown: `![](images/plot.png)`
- Ensure all referenced files are also copied to GitHub

**Large file sizes**
- Optimize images before including in HTML
- Consider using GitHub's file size limits (100MB per file)

### Checking GitHub Pages Status
1. Go to repository Settings
2. Scroll to "Pages" in left sidebar
3. Verify source is set to "Deploy from a branch: main"

---

## 📚 Example Workflow

Complete example for updating survey analysis:

```bash
# 1. In RStudio: Knit your .Rmd files to HTML

# 2. Copy files to GitHub repository
cd ~/Documents/oral-health-nutrition.github.io/COP_nutrition_survey/
cp ~/Documents/DDUH_DS/survey_analysis.html ./survey_analysis_v20.html

# 3. Update index page if needed (edit index.html)

# 4. Commit and push
git add .
git commit -m "Update survey analysis v20 with latest data"
git push origin main

# 5. Share the link
echo "https://oral-health-nutrition.github.io/COP_nutrition_survey/survey_analysis_v20.html"
```

---

## 🎯 Next Steps

1. **Clean up existing files** in your repository
2. **Create index pages** for each project folder
3. **Set up fluoride research** folder with same structure
4. **Create automation scripts** for regular updates
5. **Document your specific workflow** for future reference

---

*Last updated: 2025-06-24*  
*Repository: oral-health-nutrition.github.io*