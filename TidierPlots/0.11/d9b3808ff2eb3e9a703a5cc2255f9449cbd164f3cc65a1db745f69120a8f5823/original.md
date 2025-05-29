```
geom_smooth(aes(...), ...)
geom_smooth(plot::GGPlot, aes(...), ...)
```

Represent data as a smoothed or linear fit.

# Arguments

  * `plot::GGPlot` (optional): a plot object to add this geom to
  * `aes(...)`: the names of the columns in the DataFrame that will be used in the mapping
  * `...`: options that are not mapped to a column (passed to Makie.Lines)

# Required Aesthetics

  * `x`
  * `y`

# Optional Aesthetics (see [`aes`](@ref))

  * NA

# Optional Arguments

  * `method`: either "smooth" (default, loess fit) or "lm" (linear fit)
  * `color` / `colour`
  * `linewidth`
  * `alpha`
  * `linestyle` / `linetype`

# Examples

```julia
xs = range(0, 2pi, length=30)
ys = sin.(xs) .+ randn(length(xs)) * 0.5
df = DataFrame(x = xs, y = ys)

ggplot(df, @aes(x = x, y = y)) + geom_smooth() + geom_point()

ggplot(penguins, @aes(x = bill_length_mm, y = bill_depth_mm)) +
    geom_smooth(color=:red, linewidth=10, alpha=0.5)
```
