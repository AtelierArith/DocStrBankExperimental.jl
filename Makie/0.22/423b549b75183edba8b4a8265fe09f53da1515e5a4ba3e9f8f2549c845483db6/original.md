```
boundingbox(scenelike[, exclude = plot -> false])
```

Returns the combined data space bounding box of all plots collected under `scenelike`. This include `plot.transformation`, i.e. the `transform_func` and the `model` matrix. Plots with `exclude(plot) == true` are excluded.

See also: [`data_limits`](@ref)
