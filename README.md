# Hugo Theme Mini

English | [简体中文](https://github.com/nodejh/hugo-theme-mini/tree/master/README-zh_CN.md)

A fast, minimalist and responsive hugo theme.

![./images/screenshot.png](https://raw.githubusercontent.com/nodejh/hugo-theme-mini/master/images/screenshot.png)

- [Online demo](https://nodejh.github.io/hugo-theme-mini)
- [Example Site Source](https://github.com/nodejh/hugo-theme-mini/tree/master/exampleSite)

Features:

- Fast
- Minimalist
- Responsive
- Archive
- Tags


## 1. Installation


### 1.1 As a Hugo Module (recommended)

> ⚠️ If you installed a [Hugo binary](https://gohugo.io/getting-started/installing/#binary-cross-platform), you may not have Go installed on your machine. To check if Go is installed:
> ```
> $ go version
> ```
>  Go modules were considered production ready in v1.14. [Download Go](https://golang.org/dl/). 

1. From your project's root directory, initiate the hugo module system if you haven't already:

    ```bash
    $ hugo mod init github.com/<your_user>/<your_project>
    ```

2. Add the theme's repo to your `config.yaml`:

    ```yaml
    theme: 
       - github.com/nodejh/hugo-theme-mini
    ```

### 1.2 As Git Submodule

1. Inside the folder of your Hugo site run:

    ```bash
    $ git submodule add https://github.com/nodejh/hugo-theme-mini.git themes/mini
    ```

2. Add the theme's directory to your `config.yaml`:

    ```yaml
   theme: mini
    ```

For more information read the official [setup guide](//gohugo.io/overview/installing/) of Hugo.


## 2. Getting started

After installing the theme successfully it requires a just a few more steps to get your site running.

The theme needs Hugo 0.158.0 or newer.


### 2.1 The config file

Take a look inside the [`exampleSite`](https://github.com/nodejh/hugo-theme-mini/tree/master/exampleSite) folder of this theme. You'll find a file called [`config.yaml`](https://github.com/nodejh/hugo-theme-mini/blob/master/exampleSite/config.yaml). To use it, copy the [`config.yaml`](https://github.com/nodejh/hugo-theme-mini/blob/master/exampleSite/config.yaml) in the root folder of your Hugo site. Feel free to change the strings in this theme.

> ⚠️ You may need to delete the line: `themesDir: ../../` 

### 2.2 Default Content Language

You can set default content language by `defaultContentLanguage`:

```yaml
defaultContentLanguage: en
```

Default is `en`. Now support:

- `en`: English
- `zh`: Chinese
- `nl`: Dutch 
- `fr`: French
- `es`: Spanish

More about multiple languages: [Multilingual Mode](https://gohugo.io/content-management/multilingual/).

### 2.3 Add Comments

To enable comments, add following to your config file:

- Disqus shortname:

    ```yaml
    services:
      disqus:
        shortname: your-disqus-shortname
    ```

- Enable Comment:

    ```yaml
    params:
      enableComments: true
    ```

### 2.4 Google Analytics

To enable google analytics, add following to your config file:

- Google Analytics ID:

    ```yaml
    services:
      googleAnalytics:
        id: G-MEASUREMENT_ID
    ```

- Enable Google Analytics:

    ```yaml
    params:
      enableGoogleAnalytics: true
    ```

### 2.5 Logo and favicon

The avatar at the top of list pages and the favicon come from site params:

```yaml
params:
  avatar: /images/avatar-150.webp    # shown at 150x150
  avatar2x: /images/avatar-300.webp  # optional, for high-DPI screens
  favicon: /images/favicon-96.png
  images: ['/images/card.png']       # social card image (Open Graph / Twitter)
```

Size `avatar` for its 150px slot (and `avatar2x` at 300px); a large original here costs every visitor bytes they never see. If `avatar` or `favicon` is not set, the first entry of `images` is used, and failing that `static/images/avatar.png` and `static/images/favicon.ico`.

### 2.6 Social links

Footer icons (github, twitter, stackoverflow, facebook) are read from `params.social`. Give each network a handle, or a full URL:

```yaml
params:
  social:
    github: your-name
    twitter: your-name                  # also used for the twitter:site tag
    stackoverflow: 1234567/your-name    # the part after stackoverflow.com/users/
```

Use a handle for `twitter`: Hugo's built-in Twitter Card template reads `params.social.twitter` and prefixes it with `@`.

### 2.7 Syntax highlighting

The theme styles code with CSS classes, so that colours meet WCAG AA contrast and follow the reader's light or dark colour scheme. Turn off Chroma's inline styles:

```yaml
markup:
  highlight:
    noClasses: false
```

The palette lives in `assets/css/syntax.css`.

### 2.8 Nearly finished

In order to see your site in action, run Hugo's built-in local server.

```bash
$ hugo server
```

Now enter http://localhost:1313 in the address bar of your browser.

### 2.9 Production

To run in production (e.g. to have Google Analytics show up), run HUGO_ENV=production before your build command. For example:

```bash
HUGO_ENV=production hugo
```

Note: The above command will not work on Windows. If you are running a Windows OS, use the below command:

```bash
set HUGO_ENV=production
hugo
```


## 3. Optional Configuration

### 3.1 Table of Content

To enable table of content, you could set `showToc` to `true`.

For example:

```yaml
showToc: true
```

### 3.2 Disable Comments on a single post

You can set `enableComments` to `false` in front matter to disable disqus comments on a single post.

For example:

```yaml
---
title: Some title
enableComments: false
---
```

### 3.3 Custom CSS and JS

The theme's own stylesheet (`assets/css/style.css` and `assets/css/syntax.css`) is minified and inlined into each page, so there is no render-blocking stylesheet request. It supports light and dark colour schemes through CSS custom properties; to restyle the theme, override those properties in a custom stylesheet.

You can put your custom css and js files to `static` directory, or use remote css and js files which start with `http://` or `https://`.

For example:

```yaml
customCSS:
  - css/custom.css # local css in `static/css/custom.css`
  - https://example.com/custom.css # remote css
customJS:
  - js/custom.js # local js in `static/js/custom.js`
  - https://example.com/custom.js # remote js
```

### 3.4 Math Typesetting

Mathematical notation is enabled by [KaTeX](https://katex.org/).

- To enable KaTex globally set the parameter `math` to `true` in project’s configuration
- To enable KaTex on a per page basis include the parameter `math` to `true` in content files

### 3.5 Hidden Post Summary in Home Page 

To hidden post summary in home page, you could set `hiddenPostSummaryInHomePage` to `true`, default is `false`.

For example:

```yaml
hiddenPostSummaryInHomePage: true
```

### 3.6 Headings in content

Every page already has an `<h1>` (the post title, or the site title on list pages). If a page's markdown uses top-level headings (`# Section`) for its sections, the theme renders all of that page's headings one level down (`#` becomes `<h2>`, `##` becomes `<h3>`, and so on), so each page keeps a single `<h1>`. Markdown that starts its sections at `##` is rendered as written.

### 3.7 Images in content

Markdown images are lazy-loaded (except the first on a page) and get `width` and `height` attributes when the file is found under `static/`, which prevents layout shift while they load.

## License

[MIT](https://github.com/nodejh/hugo-theme-mini/blob/master/LICENSE.md)
