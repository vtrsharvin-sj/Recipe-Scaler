# Gather — Recipe Scaler

> Same recipe. A different table.

**[Live demo → vtrsharvin-sj.github.io/Recipe-Scaler](https://vtrsharvin-sj.github.io/Recipe-Scaler)**

**gather.** is a small kitchen companion that scales a recipe for any number of servings. Enter a dish, its original servings, and the ingredients, then choose how many people you're cooking for. It does the maths, saves your recipe in the browser, and lets you print a clean ingredient list.

It is a single HTML file with no dependencies, no build step, and no network requests, so it works offline.

<!-- Add a screenshot: ![gather. screenshot](docs/screenshot.png) -->

## Features

- **Instant scaling.** New amount = original amount × (servings wanted ÷ original servings).
- **Quick scale buttons.** One tap for ½×, 2×, or 3× the original servings.
- **Eight units.** g, kg, ml, L, tsp, tbsp, cups, pieces.
- **Auto-save.** Your recipe and last result are stored in `localStorage` and restored on refresh. Nothing leaves your browser.
- **Print-friendly.** A dedicated print stylesheet hides everything except the scaled recipe card.
- **Input validation.** Clear inline messages for empty names, invalid numbers, or values outside the supported range.
- **Accessible.** Labelled inputs, `aria-live` results, `role="alert"` errors, visible focus states, and `aria-invalid` on problem fields.
- **Responsive.** Layouts for desktop, tablet, and phone.
- **Graceful fallback.** If browser storage is unavailable, the app keeps working and tells you to keep the tab open.

## Getting started

The quickest way to try it is the [live site](https://vtrsharvin-sj.github.io/Recipe-Scaler). To run it locally, no installation is required:

```bash
git clone https://github.com/vtrsharvin-sj/Recipe-Scaler.git
cd Recipe-Scaler
open index.html   # or just double-click the file
```

## How to use

1. **Start with what you know.** Enter the dish name, original servings, and servings wanted.
2. **Add your ingredients.** Fill in the name, amount, and unit for each of the three ingredient rows. Click **Try an example ↗** to load a sample recipe.
3. **Scale it.** Press **Scale my recipe** and the adjusted amounts appear on the recipe card.
4. **Print or come back later.** Use **Print recipe ↗**, or reload the page and your last result will still be there.

### Example

| Ingredient | Original (2 servings) | Scaled (6 servings) |
| ---------- | --------------------- | ------------------- |
| Rice       | 200 g                 | 600 g               |
| Water      | 400 ml                | 1,200 ml            |
| Vegetables | 100 g                 | 300 g               |

## Project structure

```
.
├── index.html   # markup, styles, and logic in one file
└── README.md
```

## Tech notes

- Plain HTML, CSS, and vanilla JavaScript (strict mode).
- Recipe state is saved under the `gather.recipe.v1` key in `localStorage`.
- Numbers are formatted with `Intl.NumberFormat` (up to 3 decimal places). Very small or very large results switch to exponential notation.
- Results are rendered with `textContent` and DOM APIs rather than `innerHTML`, so user input is never interpreted as HTML.

## Limitations

- Each recipe has exactly three ingredient rows.
- Amounts scale proportionally. Salt, spices, and cooking times often need tasting and adjusting rather than straight multiplication.
- Units are not converted (for example, tbsp to ml); amounts keep the unit you chose.

## Roadmap ideas

- Add and remove ingredient rows
- Unit conversion (metric ↔ US)
- Multiple saved recipes
- Installable PWA with a service worker

## Contributing

Issues and pull requests are welcome. Because the project is a single file, you can open `index.html` in a browser to test changes directly.

## License

Released under the [MIT License](LICENSE). Update this section if you choose a different license.
