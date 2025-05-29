```
colormap!(p, cmap)
```

Apply a colormap `cmap` to the given plot `p`, which can be a `PlotObject`, or a `Figure` (in such case the colormap is applied to all the plots contained in it).

The value of `cmap` can be the number or the name of any of the [GR built-in colormaps](https://gr-framework.org/colormaps.html) (see [`colormap`](@ref) for more details).

Use the keyword argument `colormap` in plotting functions, to set a particular colormap during the creation of plots (in this case it can only be identified by its number).

# Examples

```julia
# Create a surface plot with the "grayscale" colormap (2)
surface(x, y, z, colormap=2)
# Change it to the "viridis" colormap
colormap!(gcf(), "viridis")
```
