```
geom_path(aes(...), ...)
geom_path(plot::GGPlot, aes(...), ...)
```

Represents data as connected points in the order in which they appear in the data.

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
ggplot(penguins, @aes(x = bill_length_mm, y = bill_depth_mm)) +
    geom_path()
```
