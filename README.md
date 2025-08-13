# SEO Analysis and Link Checker
A Python 3 tool for comprehensive website SEO analysis and link validation with support for sitemaps, multiple output formats, and multi-threading for faster crawling.

## Features
- **SEO Analysis**: Word count, page titles, meta descriptions, keyword extraction, and SEO warnings
- **Link Analysis**: HTTP status code validation and broken link detection
- **Sitemap Support**: Analyze all URLs listed in XML sitemaps
- **Multiple Output Formats**: HTML and JSON reporting
- **Multi-threading**: Faster crawling with configurable worker threads
- **Flexible Link Types**: Analyze different types of links (anchor tags, images, scripts, stylesheets)

## Installation

### Requirements
- Python 3.x
- Required dependencies: `requests`, `beautifulsoup4`

### Install Dependencies

#### Using requirements.txt (Recommended)
```bash
# Create a virtual environment
python -m venv seo_env

# Activate the virtual environment
# On Windows:
seo_env\Scripts\activate
# On macOS/Linux:
source seo_env/bin/activate

# Install dependencies from requirements.txt
pip install -r requirements.txt
```

#### Manual Installation
```bash
pip install requests beautifulsoup4
```

## Usage

### Basic Usage
Simple SEO and link analysis of a single URL with JSON output (default):
```bash
python seo_link_analyzer.py https://example.com
```

### Using Sitemaps
Analyze all URLs listed in a sitemap:
```bash
python seo_link_analyzer.py https://example.com --sitemap https://example.com/sitemap.xml
```

### Output Options

#### JSON Output (Default)
```bash
python seo_link_analyzer.py https://example.com --output-format json
```

#### HTML Output
```bash
python seo_link_analyzer.py https://example.com --output-format html
```

The HTML output provides a comprehensive, styled report with detailed SEO analysis and link validation results. The report includes interactive sections for easy navigation and visual indicators for broken links and SEO issues.

*[Screenshot placeholder: HTML output report showing SEO analysis dashboard with color-coded link status, keyword density charts, and detailed recommendations]*

#### Save to File
```bash
python seo_link_analyzer.py https://example.com --output-format html --output-file report.html
```

### Link Types
Specify which types of links to analyze using `--link-types`:
- `a` - Anchor tags (links)
- `img` - Image tags
- `script` - Script tags
- `link` - Link tags (CSS, etc.)

#### Examples:
```bash
# Analyze only anchor tags (default)
python seo_link_analyzer.py https://example.com --link-types a

# Analyze both anchor tags and images
python seo_link_analyzer.py https://example.com --link-types a img

# Analyze all link types
python seo_link_analyzer.py https://example.com --link-types a img script link
```

### Performance Options

#### Multi-threading
Control the number of worker threads for faster analysis:
```bash
python seo_link_analyzer.py https://example.com --workers 8
```

#### Show Progress
Display progress information during analysis:
```bash
python seo_link_analyzer.py https://example.com --progress
# or
python seo_link_analyzer.py https://example.com -p
```

### Complete Example
Comprehensive analysis with all options:
```bash
python seo_link_analyzer.py https://example.com \
  --sitemap https://example.com/sitemap.xml \
  --link-types a img \
  --output-format html \
  --output-file report.html \
  --workers 8 \
  --progress
```

## Output Information
The script provides detailed reports including:

### SEO Analysis
- Page word count
- Title tag analysis
- Meta description evaluation
- Keyword extraction
- SEO warnings and recommendations
- Missing or duplicate titles/descriptions
- Missing image alt text

### Link Analysis
- HTTP status codes for all links
- Broken link identification (4xx/5xx errors)
- Connection error detection
- Source page information for each broken link

## Command Line Options
```
positional arguments:
  url                   The URL to analyze

optional arguments:
  --sitemap SITEMAP     XML sitemap URL to analyze all listed URLs
  --link-types {a,img,script,link} [{a,img,script,link} ...]
                       Types of links to analyze (default: a)
  --output-format {json,html}
                       Output format (default: json)
  --output-file OUTPUT_FILE
                       Save output to specified file
  --no-links           Skip link analysis, perform SEO analysis only
  --workers WORKERS    Number of worker threads (default: 4)
  --progress, -p       Show progress during analysis
```

## License
This project is open source and available under the MIT License.
