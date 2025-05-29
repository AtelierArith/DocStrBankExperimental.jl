```
fuzzy_cmeans(data::AbstractMatrix, C::Integer, fuzziness::Real;
             [dist_metric::SemiMetric], [...]) -> FuzzyCMeansResult
```

Perform Fuzzy C-means clustering over the given `data`.

# Arguments

  * `data::AbstractMatrix`: $d×n$ data matrix. Each column represents one $d$-dimensional data point.
  * `C::Integer`: the number of fuzzy clusters, $2 ≤ C < n$.
  * `fuzziness::Real`: clusters fuzziness ($μ$ in the [mathematical formulation](@ref fuzzy_cmeans_def)), $μ > 1$.

Optional keyword arguments:

  * `dist_metric::SemiMetric` (defaults to `Euclidean`): the `SemiMetric` object  that defines the distance between the data points
  * `maxiter`, `tol`, `display`, `rng`: see [common options](@ref common_options)
