```
geom_col(aes(...), ...)
geom_col(plot::GGPlot, aes(...), ...)
```

Represent data as columns.

# Details

The columns are stacked by default, and the behavior can be changed with the "position" argument. The position can either be "stack" or "dodge". If the argument is "dodge", then a a grouping variable will also need to be supplied to `aes`. Alternatively you can supply the grouping variable to `dodge` within the aesthetic.

# Arguments

  * `plot::GGPlot` (optional): a plot object to add this geom to
  * `aes(...)`: the names of the columns in the DataFrame that will be used in the mapping
  * `...`: options that are not mapped to a column (passed to Makie.BarPlot)

# Required Aesthetics

  * `x`
  * `y`

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
df = @chain penguins begin
    @group_by(species, sex)
    @summarize(mean_bill_length_mm = mean(bill_length_mm))
    @ungroup()
end

ggplot(df) +
    geom_col(@aes(x = species, y = mean_bill_length_mm))

# dodge using the group and position arguments
ggplot(df) +
    geom_col(@aes(x = species, y = mean_bill_length_mm, group = sex),
             position="dodge")

# dodge using the dodge aesthetic
ggplot(df) +
    geom_col(@aes(x = species, y = mean_bill_length_mm, dodge = sex))

# color based on grouping variable
ggplot(df) +
    geom_col(@aes(x = species, y = mean_bill_length_mm, color = sex))
```
