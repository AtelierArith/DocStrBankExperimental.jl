```
data_limits(scenelike[, exclude = plot -> false])
```

Returns the combined data limits of all plots collected under `scenelike` for which `exclude(plot) == false`. This is solely based on the positional data of a plot and thus does not include any transformations.

See also: [`boundingbox`](@ref)
