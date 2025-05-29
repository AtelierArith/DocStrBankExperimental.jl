```
geom_errorbarh(aes(...), ...)
geom_errorbarh(plot::GGPlot, aes(...), ...)
```

Represents data as a horizontal interval.

# Arguments

  * `plot::GGPlot` (optional): a plot object to add this geom to
  * `aes(...)`: the names of the columns in the DataFrame that will be used in the mapping
  * `...`: options that are not mapped to a column (passed to Makie.Rangebars)

# Required Aesthetics

  * `y`
  * `xmin`
  * `xmax`

# Optional Aesthetics (see [`aes`](@ref))

  * NA

# Optional Arguments

  * `color` / `colour`
  * `direction=:x`
  * `linewidth`
  * `whiskerwidth` / `width`

# Examples

```julia
df = DataFrame(
    trt   = [1, 1, 2, 2],
    resp  = [1, 5, 3, 4],
    group = [1, 2, 1, 2],
    lower = [0.8, 4.6, 2.4, 3.6],
    upper = [1.1, 5.3, 3.3, 4.2],
)

ggplot(df, @aes(y = trt, xmin = lower, xmax = upper)) +
    geom_errorbarh(linewidth=2)
```
