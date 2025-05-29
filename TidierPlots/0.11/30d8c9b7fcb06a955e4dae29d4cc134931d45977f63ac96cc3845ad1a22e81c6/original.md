```
geom_hline(aes(...), ...)
geom_hline(plot::GGPlot, aes(...), ...)
```

Plot a horizontal line at the given y-intercept(s).

# Arguments

  * `plot::GGPlot` (optional): a plot object to add this geom to
  * `aes(...)`: the names of the columns in the DataFrame that will be used in the mapping
  * `...`: options that are not mapped to a column (passed to Makie.HLines)

# Required Aesthetics

  * NA

# Optional Aesthetics (see [`aes`](@ref))

  * `yintercept(s)`
  * `color` / `colour`

# Optional Arguments

  * `yintercept(s)`
  * `color` / `colour`
  * `linewidth`
  * `linestyle` / `linetype`
  * `colormap` / `palette`
  * `alpha`

# Examples

```julia
# Plot only a single y-intercept
ggplot() + geom_hline(yintercept = 3)

# Plot multiple y-intercepts
ggplot() + geom_hline(yintercept = [-1, 4])

# Plot multiple y-intercepts mapped to a column
df = DataFrame(y = rand(4))
ggplot(df, @aes(yintercept = y)) + geom_hline()
```
