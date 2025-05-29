```
geom_vline(aes(...), ...)
geom_vline(plot::GGPlot, aes(...), ...)
```

Plot a horizontal line at the given y-intercept(s).

# Arguments

  * `plot::GGPlot` (optional): a plot object to add this geom to
  * `aes(...)`: the names of the columns in the DataFrame that will be used in the mapping
  * `...`: options that are not mapped to a column (passed to Makie.VLines)

# Required Aesthetics

  * NA

# Optional Aesthetics (see [`aes`](@ref))

  * `xintercept(s)`
  * `color` / `colour`

# Optional Arguments

  * `xintercept(s)`
  * `color` / `colour`
  * `linewidth`
  * `linestyle` / `linetype`
  * `colormap` / `palette`
  * `alpha`

# Examples

```julia
# Plot only a single x-intercept
ggplot() + geom_vline(xintercept = 3)

# Plot multiple x-intercepts
ggplot() + geom_vline(xintercept = [-1, 4])

# Plot multiple x-intercepts mapped to a column
df = DataFrame(x = rand(4))
ggplot(df, @aes(xintercept = x)) + geom_vline()
```
