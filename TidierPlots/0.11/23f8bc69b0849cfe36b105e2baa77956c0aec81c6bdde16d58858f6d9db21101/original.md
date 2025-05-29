```
geom_bar(aes(...), ...)
geom_bar(plot::GGPlot, aes(...), ...)
```

Represent the counts of a grouping variable as columns.

# Details

The columns are stacked by default, and the behavior can be changed with the "position" argument. The position can either be "stack" or "dodge". If the argument is "dodge", then a a grouping variable will also need to be supplied to `aes`. Alternatively you can supply the grouping variable to `dodge` within the aesthetic.

# Arguments

  * `plot::GGPlot` (optional): a plot object to add this geom to
  * `aes(...)`: the names of the columns in the DataFrame that will be used in the mapping
  * `...`: options that are not mapped to a column (passed to Makie.BarPlot)

# Required Aesthetics

  * `x` OR `y` (not both)

# Optional Aesthetics (see [`aes`](@ref))

  * `color` / `colour`
  * `strokecolor` / `strokecolour`
  * `dodge`
  * `group`

# Optional Arguments

  * `position`: "stack" (default) or "dodge"
  * `stroke` / `strokewidth`
  * `strokecolor` / `strokecolour`
  * `direction`: `:y` (default) or :x
  * `dodge_gap`
  * `gap`

# Examples

```julia
# vertical bar plot
ggplot(penguins) + geom_bar(@aes(x = species))

# horizontal bar plot
ggplot(penguins) + geom_bar(@aes(y = species))

# stacked
ggplot(penguins, @aes(x = species, fill=sex)) + geom_bar()

# dodged
ggplot(penguins, @aes(x = species, fill=sex, dodge = sex)) + geom_bar()
```
