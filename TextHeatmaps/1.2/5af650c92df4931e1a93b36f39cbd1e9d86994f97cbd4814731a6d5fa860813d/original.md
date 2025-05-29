```
heatmap(values::AbstractArray, words)
```

Create a heatmap of words where the background color of each word is determined by its corresponding value. Arguments `values` and `words` (and optionally `colors`) must have the same size.

## Keyword arguments

  * `colorscheme::Union{ColorScheme,Symbol}`: color scheme from ColorSchemes.jl. Defaults to `ColorSchemes.seismic`.
  * `rangescale::Symbol`: selects how the color channel reduced heatmap is normalized before the color scheme is applied. Can be either `:extrema` or `:centered`. Defaults to `:centered` for use with the default color scheme `seismic`.
