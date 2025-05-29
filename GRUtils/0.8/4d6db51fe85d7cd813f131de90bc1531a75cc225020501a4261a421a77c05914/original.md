```
aspectratio(r)
```

Set the aspect of the current plot to a given width : height ratio.

Use the keyword argument `aspectratio=r`, etc. in plotting functions, to set the aspect ratio during the creation of plots.

# Examples

```julia
# Create example data
x = LinRange(-2, 2, 40)
y = x.^3 .+ x.^2 .+ x
# Draw a plot with panoramic ratio (16:9)
plot(x, y)
aspectratio(16/9)

```
