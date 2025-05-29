```
Interpolate(domain; [options])
```

Interpolate geotable on given `domain` (or vector of geometries) using a set of `options`.

## Options

  * `model` - Model from GeoStatsModels.jl (default to `NN()`)
  * `point` - Perform interpolation on point support (default to `true`)
  * `prob`  - Perform probabilistic interpolation (default to `false`)

## Examples

```julia
# nearest neighbor model
Interpolate(grid, model=NN())

# inverse distance weighting model
Interpolate(pset, model=IDW())
```

### Notes

The interpolation is performed with all the samples (i.e. rows of the geotable) at once, which can be prohibitive for some models like Kriging. If that is the case, prefer [`InterpolateNeighbors`](@ref).

See also [`InterpolateNeighbors`](@ref).
