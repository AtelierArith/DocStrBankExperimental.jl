```
localanisotropies(Gradients, grid, propname, w)
```

Extract `LocalAnisotropy` from a reference scenario. The `propname` variable from the cartesian `grid` object is scanned and local gradients are extracted from it. These gradients are smoothed within a squared/cubic window sized 2`w` x 2`w` (x 2`w`) in order to return an ellipse/ellipsoid along the directions with more/less variability (`w` must be an `Int` value and corresponds to the number of grid cells). A preliminar magnitude is also extracted from it and can be later rescaled to proper limits using [`rescale_magnitude`](@ref) function.

## Example

```julia
lpars = localanisotropies(Gradients, grid, :CO2, 5)
```
