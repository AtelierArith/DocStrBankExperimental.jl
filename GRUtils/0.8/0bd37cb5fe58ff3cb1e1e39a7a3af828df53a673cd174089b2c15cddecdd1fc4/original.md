```
annotations(x, y, s; kwargs...)
```

Add one ore more text annotations to the current plot.

`x` and `y` can be scalars or vectors of coordinates, and `s` a string or a vector of strings, respectively. Annotations are only available for 2-D plots.

By default the coordinates indicate the lower left corner of the text box. This can be changed by the following keyword arguments:

  * `halign` for the horizontal alignment (`"left"`, `"center"` or `"right"`).
  * `valign` for the vertical alignment (`"bottom"`, `"center"` or `"top"`).

Use the keyword argument `wc = false` if `x` and `y` are expressed in normalized device coordinates, instead of world coordinates – which is the default.

# Examples

```julia
# Create example data
numbers = [10, 15, 35, 20]
# Plot bars with labels on top
barplot(numbers)
annotations(1:4, numbers .+1 , string.(numbers), halign="center")

```
