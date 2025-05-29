```
geom_line(aes(...), ...)
geom_line(plot::GGPlot, aes(...), ...)
```

Represents data as connected points in the order of the variable on the x-axis.

# Arguments

  * `plot::GGPlot` (optional): a plot object to add this geom to
  * `aes(...)`: the names of the columns in the DataFrame that will be used in the mapping
  * `...`: options that are not mapped to a column (passed to Makie.Lines)

# Required Aesthetics

  * `x`
  * `y`

# Optional Aesthetics (see [`aes`](@ref))

  * `color` / `colour`

# Optional Arguments

  * `color` / `colour`
  * `colormap` / `palette`
  * `linestyle` / `linetype`
  * `linewidth`
  * `alpha`

# Examples

```julia
xs = range(0, 2pi, length=30)
df = DataFrame(x = xs, y = sin.(xs))

ggplot(df, @aes(x = x, y = y)) + geom_line()
```
