```
`csscolors(name, color)`
`csscolors(names, colors)`
`csscolors(prefix, colors)`
```

Construct a css string that defines colors to be used for styling quasar elements; either as a value for the keyword argument `color` or as a classname with the resective prefix `text-` or `bg-`. (cf. [quasar docs](https://quasar.dev/style/color-palette))

# Usage

css = style(csscolors(:stipple, [RGB(0.2, 0.4, 0.8), "#123456", RGBA(0.1, 0.2, 0.3, 0.5)]))

ui(model) = css * page(model, class="container, text-stipple-1", [   btn("Hit me", @click(:pressed), color="stipple-3") ])
