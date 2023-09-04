# tailwind-css-examples

## example-01-normal

This is how you normally use tailwind (aka Tailwind CLI).
This project is a simple html project

First, install Tailwind

```sh
pnpm add -D tailwindcss
```

Create a config file, using TW CLI

```sh
pnpx tailwindcss init
```

List the files you want TW to look at for TW classes

```js
// twind.config.js
/** @type {import('tailwindcss').Config} */
module.exports = {
  content: ["./src/**/*.{html,js}"],
  theme: {
    extend: {},
  },
  plugins: [],
};
```

The above sets up TW to look in the src folder and scan html and js files for tailwind classes.

Create the base tailwind css file

```sh
touch ./src/app.css
```

Add base styles

```css
/* app.css  */
@tailwind base;
@tailwind components;
@tailwind utilities;
```

Now whenever you to generate you css styles, run:

```sh
pnpm tailwindcss -i ./src/app.css -o ./dist/app.css -c ./tailwind.config.js --minify
```

## example-02-vite

Vite is the tool used for web development.
Vite works sort of like a bundler, which takes js/ts and css/scss/less files and compile them to web compliant files to work with your html.
You can have multiple script and style files which will be compiled into single files, for eg.

```
# input files
functions.js
utilities.ts
style.less
variables.scss

# output files
app.css
app.min.css
app.min.css.map

app.js
app.min.js
app.min.js.map
```

Vite however only bundles all your code when you build a website for publishing.
Vite does not bundle your code during development.

Vite is very popular now (the successor to Webpack), so this example is included to show how you would integrate tailwind with a vite project.

Create a new vite project:

```sh
pnpm create vite@latest <project-name> -- --template vanilla-ts
```

Example:

```sh
pnpm create vite@latest .\packages\example-02-vite -- --template vanilla-ts
```

Note the `--template vanilla-ts` at the end.
Vite can be used to create other framework project types, such as svelte, react, angular and vue.
We just use the framework-less vanilla-ts template.
