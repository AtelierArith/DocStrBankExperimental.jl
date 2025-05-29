```
violin(x, y; kwargs...)
```

Draw a violin plot.

# Arguments

  * `x`: positions of the categories
  * `y`: variables whose density is computed

# Keywords

  * `weights`: vector of statistical weights (length of data). By default, each observation has weight `1`.
  * `orientation=:vertical`: orientation of the violins (`:vertical` or `:horizontal`)
  * `width=1`: width of the box before shrinking
  * `gap=0.2`: shrinking factor, `width -> width * (1 - gap)`
  * `show_median=false`: show median as midline
  * `side=:both`: specify `:left` or `:right` to only plot the violin on one side
  * `datalimits`: specify values to trim the `violin`. Can be a `Tuple` or a `Function` (e.g. `datalimits=extrema`)
