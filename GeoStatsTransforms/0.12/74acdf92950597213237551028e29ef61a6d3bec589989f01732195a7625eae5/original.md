```
InterpolateNeighbors(domain; [options])
```

Interpolate geotable with neighbor search on given `domain` (or vector of geometries) using a set of `options`.

## Options

  * `model`        - Model from GeoStatsModels.jl (default to `NN()`)
  * `path`         - Path over the domain (default to `LinearPath()`)
  * `point`        - Perform interpolation on point support (default to `true`)
  * `prob`         - Perform probabilistic interpolation (default to `false`)
  * `minneighbors` - Minimum number of neighbors (default to `1`)
  * `maxneighbors` - Maximum number of neighbors (default to `10`)
  * `neighborhood` - Search neighborhood (default to `nothing`)
  * `distance`     - A distance defined in Distances.jl (default to `Euclidean()`)

Two neighbor search methods are available:

  * If a `neighborhood` is provided, local prediction is performed  by sliding the `neighborhood` in the domain (e.g. `MetricBall`).
  * If a `neighborhood` is not provided, the prediction is performed  using `maxneighbors` nearest neighbors according to `distance`.

## Examples

```julia
# polynomial model with 10 nearby samples
InterpolateNeighbors(grid, model=Polynomial(), maxneighbors=10)

# inverse distance weighting model with samples inside 100m radius
InterpolateNeighbors(pset, model=IDW(), neighborhood=MetricBall(100u"m"))
```

### Notes

The interpolation is performed with a subset of nearby samples. This can lead to undesired artifacts, specially when the number of samples is small. If that is that case, prefer [`Interpolate`](@ref).

See also [`Interpolate`](@ref).
