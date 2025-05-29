```
violin(x, y; kwargs...)
```

Draw a violin plot.

# Arguments

  * `x`: positions of the categories
  * `y`: variables whose density is computed

# Keywords

  * `orientation=:vertical`: orientation of the violins (`:vertical` or `:horizontal`)
  * `width=0.8`: width of the violin
  * `show_median=true`: show median as midline
  * `side=:both`: specify `:left` or `:right` to only plot the violin on one side
  * `datalimits`: specify values to trim the `violin`. Can be a `Tuple` or a `Function` (e.g. `datalimits=extrema`)
