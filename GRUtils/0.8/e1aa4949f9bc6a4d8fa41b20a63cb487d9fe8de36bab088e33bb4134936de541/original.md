```
background(color[, alpha])
```

Add a custom background color to the current figure.

The argument can be an hexadecimal color code or `nothing` for a transparent background. A partially transparent color can be defined adding the alpha value between 0 and 1 as second argument.

Use the keyword arguments `backgroundcolor` and `backgroundalpha` in plotting functions, to set a particular background color configuration during the creation of plots.

This overrides the default background defined by the [`colorscheme`](@ref) for the area outside the axes and legends of all the plots contained in the figure. Use [`background!`](@ref) to modify the background of individual subplots.

# Examples

```julia
# Create a plot with light blue background
plot(x, y, backgroundcolor=0x88ccff)
# Remove the background
background(nothing)
```
