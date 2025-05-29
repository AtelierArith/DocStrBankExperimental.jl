```
cgrad(colors, [values]; categorical = nothing, scale = nothing, rev = false, alpha = nothing)
```

Construct a Colorgradient from `colors` and `values`.

`colors` can be a symbol for ColorSchemes.jl `ColorScheme`s, a `ColorScheme`, a vector of colors, a `ColorGradient` or a `ColorPalette`. If `values` is an integer, it specifies the numbers of colors chosen equidistantly from the colorscheme specified by colors. Otherwise vectors are accepted. For continuous color gradients `values` indicate where between 0 and 1 the colors are positioned. For categorical color gradients `values` indicate where a color ends and where a new one begins between 0 and 1. 0 and 1 are added to `values` if not already present.

If `rev` is `true` colors are reversed. `scale` accepts the symbols `:log`, `:log10`, `:log2`, `:ln`, `:exp`, `:exp10` or functions. If `alpha` is set, it is applied to all colors.
