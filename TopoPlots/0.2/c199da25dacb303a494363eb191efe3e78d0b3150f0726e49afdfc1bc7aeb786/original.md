```
GeomExtrapolation(
    method = Shepard(), # extrapolation method
    geometry = Rect, # the geometry to fit around the points
    enlarge = 3.0 # the amount to grow the bounding geometry for adding the extra points
)
```

Takes positions and data, and returns points and additional datapoints on an enlarged bounding geometry:

```julia
extra = GeomExtrapolation()
extra_positions, extra_data, bounding_geometry, bounding_geometry_enlarged = extra(positions, data)
```
