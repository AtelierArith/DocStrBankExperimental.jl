```
geom_text(aes(...), ...)
geom_text(plot::GGPlot, aes(...), ...)
```

Plot text on a graph.

# Arguments

  * `plot::GGPlot` (optional): a plot object to add this geom to
  * `aes(...)`: the names of the columns in the DataFrame that will be used in the mapping
  * `...`: options that are not mapped to a column (passed to Makie.Text)

# Required Aesthetics

  * `x`
  * `y`
  * `text`

# Optional Aesthetics (see [`aes`](@ref))

  * `color` / `colour`

# Optional Arguments

  * `color` / `colour`
  * `colormap` / `palette`
  * `align`: tuple of positions (e.g. `(:left, :bottom)`)
  * `font`
  * `justification`
  * `rotation`
  * `fontsize`
  * `strokewidth`
  * `strokecolor`
  * `glowwidth` / `glow`
  * `glowcolor` / `glowcolour`
  * `word_wrap_width`
  * `alpha`

# Examples

```julia
df = DataFrame(
    x = [1,1,2,2],
    y = [1,2,1,2],
    t = ["A", "B", "C", "D"]
)

ggplot(df, @aes(x=x, y=y, text=t, color=t)) + geom_text()

ggplot(df, @aes(x=x, y=y, color=t)) +
    geom_text(@aes(text=t), fontsize=24, align=(:left, :bottom), font=:bold) +
    geom_point() +
    lims(x = (0, 3), y = (0, 3))
```
