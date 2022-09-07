# Smooth for Zola

Smooth is a responsive, semantic HTML theme for [Zola]((https://www.getzola.org/)) with no NPM dependencies, using modern CSS features such as CSS grids and flexboxes.

## Features
- Custom navigation
- Custom footer info box
- Enable/disable footer menu
- Custom footer menu links
- ... more to come

This theme is a work in progress, but you can get it up and running for your own site.

## Quickstart
### Requirements
- [Zola](https://www.getzola.org/)
- ... and that's it!

### Instructions
Here's how you can get it up and running quickly:
```bash
git clone https://github.com/rhyses-pieces/smooth-theme.git
cd smooth
zola serve
```

## Structure
Here's what your `content` folder could look like with both portfolio posts and blog posts:
```
content/
├── portfolio/
│   ├── project-1/
│   │   ├── index.md
│   │   ├── asset-1.png
│   │   └── asset-2.png
│   └── project-2/
│       ├── index.md
│       ├── asset-3.png
│       └── asset-4.png
├── blog/
│   ├── _index.md
│   ├── post-1.md
│   └── post-2.md
├── about.md
└── contact.md
```

### Portfolio
Each portfolio post lives in its own folder with an `index.md` file and several asset files to display images. There are shortcodes to make displaying images easy.

Here's an example for `project-1`:
```md
{{ figure(path="asset-1.png", width=350, alt="An asset for Project 1"), caption="More info about the asset" }}
```

In the `figure` shortcode, you need:
- a relative path to the image asset
- a set width in pixels
- alt text for your image asset
- a caption to describe your image asset

You can use frontmatter to quickly describe your portfolio piece very easily. Here's an example of frontmatter for a portfolio post:
```md
+++
title = "Project title here"
date = 2022-09-16
description = "A description of the project here. It's best if this is one sentence."
[taxonomies]
technologies = [
    "Angular",
    "NodeJS",
    "Webpack",
]
year = ["2022"]
+++
```

## Customization

To customize the theme for your own site, you'll need to reference the `theme.toml` and `config.toml`.

### Configuration

The `theme.toml` will have the base settings that are available for customization, as shown here:
```TOML
[extra]
smooth_main_menu_links = []
smooth_footer_description = """
"""
smooth_footer_menu = false
smooth_footer_links = []
```

You'll need to copy-paste the above into your own `config.toml`.

Here's an example of custom navigation and custom footer:
```TOML
[extra]
smooth_main_menu_links = [
  { name = "home", url = "/" },
  { name = "about", url = "/about/" },
  { name = "blog", url = "/blog/" },
  { name = "portfolio", url = "/portfolio/" },
  { name = "contact", url = "/contact/" },
]
smooth_footer_description = """
# Hello!

You can use markdown here in this description and it will be *automatically* parsed. How **cool** is that!
"""
smooth_footer_menu = true
smooth_footer_links = [
  { social = "GitHub", url = "https://github.com" },
  { social = "LinkedIn", url = "https://linkedin.com" },
  { social = "Twitter", url = "https://twitter.com" },
  { social = "YouTube", url = "https://youtube.com" },
]
```

#### Important Note

There is custom taxonomies that are required for this theme to work, since it's used in frontmatter. Please copy and paste the below as is into your `config.toml` above the `[extra]` section.
```TOML
taxonomies = [
    { name = "technologies" },
    { name = "year", feed = true }
]
```

### Styling
You can reference the `_variables.scss` file under the `sass` folder to quickly change styling settings for the entire site. However, the styling is still very much a work in progress, so this section is considered **unstable** until styling is *mostly* finished.

Many considerations for accessibility were taken into consideration while styling this theme. Dark mode will be considered, but it has not been implmented yet. `@media prefers-reduced-motion` will also be considered, but will depend on if animations are implemented into the theme.

## Contributing
Please feel free to send feedback and suggestions by [starting an issue](https://github.com/rhyses-pieces/smooth-theme/issues). Pull requests are also welcome!
