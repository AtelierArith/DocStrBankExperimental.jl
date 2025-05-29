```
get_color(var <: AbstractArray, range_var, colormap=colorschemes[:viridis])
get_color(var, range_var, colormap=colorschemes[:viridis])
```

Map value(s) to colors from a colormap based on a range of values

# Arguments

  * `var`: value(s) to map to colors
  * `range_var`: range of values to map to colors
  * `colormap`: colormap to use

# Returns

  * `color`: color(s) corresponding to `var`

# Examples

```julia using Colors

get*color(1, 1:2, colormap = colorschemes[:viridis]) # returns RGB{N0f8}(0.267004,0.00487433,0.329415) get*color(1:2, 1:10, colormap = colorschemes[:viridis]) # returns RGB{N0f8}(0.267004,0.00487433,0.329415) get_color(1:2, 1:10, 1, colormap = colorschemes[:viridis]) # returns RGB{N0f8}(0.267004,0.00487433,0.329415)
