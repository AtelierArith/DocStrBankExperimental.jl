```
SEQSIM(; [options])
```

The sequential simulation method introduced by Gomez-Hernandez 1993.

The method traverses all elements (i.e. geometries) of the simulation domain according to a path, approximates the conditional distribution with a set of neighbors using a geostatistical model, and assigns a value to the current element by sampling from the conditional distribution.

## Options

  * `path`         - Simulation path (default to `LinearPath()`)
  * `minneighbors` - Minimum number of neighbors (default to `1`)
  * `maxneighbors` - Maximum number of neighbors (default to `26`)
  * `neighborhood` - Search neighborhood (default to `:range`)
  * `distance`     - Distance for nearest neighbors (default to `Euclidean()`)

The conditional distribution is approximated based on a number `n` of neighbors such that `minneighbors` ≤ `n` ≤ `maxneighbors`.

The `neighborhood` can be a `MetricBall`, the symbol `:range` or `nothing`. The symbol `:range` is converted to `MetricBall(range(f))` where `f` is the geostatistical function of the geostatistical process. If `neighborhood` is `nothing`, find the nearest neighbors according to the given `distance`.

## References

  * Gomez-Hernandez & Journel 1993. [Joint Sequential Simulation of MultiGaussian Fields](https://link.springer.com/chapter/10.1007/978-94-011-1739-5_8)

### Notes

This method is very sensitive to neighbor search options and simulation path. Care must be taken to make sure that enough neighbors are used in the underlying geostatistical model.
