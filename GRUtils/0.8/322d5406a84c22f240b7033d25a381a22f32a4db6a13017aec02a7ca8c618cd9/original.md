```
zoom(r)
```

Zoom the plot by the ratio indicated by `r`.

In two-dimensional plots, the "zoomed" axes are centered around the same point, but proportionally resized to `r` times the original size.

In three-dimensional scenes defined with "camera" settings (e.g. in [`isosurface`](@ref) plots), the camera distance is divided by `r`.

# Examples

```julia
# Reduce the axes to half their size
zoom(0.5)
```
