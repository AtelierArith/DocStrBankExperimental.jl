```
LocalSGS(; [paramaters])
LocalSGS(localaniso; [paramaters])
LocalSGS(method, localaniso; [paramaters])
```

The sequential process method introduced by Gomez-Hernandez 1993. It traverses all locations of the geospatial domain according to a path, approximates the conditional Gaussian distribution within a neighborhood using simple Kriging, and assigns a value to the center of the neighborhood by sampling from this distribution.

## Parameters

  * `path`         - Process path (default to `LinearPath()`)
  * `minneighbors` - Minimum number of neighbors (default to `1`)
  * `maxneighbors` - Maximum number of neighbors (default to `36`)
  * `neighborhood` - Search neighborhood (default to `:range`)
  * `distance`     - Distance used to find nearest neighbors (default to `Euclidean()`)
  * `init`         - Data initialization method (default to `NearestInit()`)

For each location in the process `path`, a maximum number of neighbors `maxneighbors` is used to fit the conditional Gaussian distribution. The neighbors are searched according to a `neighborhood`.

The `neighborhood` can be a `MetricBall`, the symbol `:range` or `nothing`. The symbol `:range` is converted to `MetricBall(range(γ))` where `γ` is the variogram of the Gaussian process. If `neighborhood` is `nothing`, the nearest neighbors are used without additional constraints.

## References

  * Gomez-Hernandez & Journel 1993. [Joint Sequential Simulation of MultiGaussian Fields](https://link.springer.com/chapter/10.1007/978-94-011-1739-5_8)

### Notes

  * This method is very sensitive to the various parameters. Care must be taken to make sure that enough neighbors are used in the underlying Kriging model.
