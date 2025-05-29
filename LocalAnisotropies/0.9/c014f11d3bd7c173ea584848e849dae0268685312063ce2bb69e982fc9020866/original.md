```
LocalInterpolate(params ...)
```

Example: MW = LocalKriging(:MovingWindows, lpars, γ) data |> Select(:var) |> LocalInterpolate(domain, model=MW, kwargs...)

## Keyword Parameters

  * `point`            - Perform interpolation on point support (default to `true`)
  * `prob`             - Perform probabilistic interpolation (default to `false`)
  * `get_only_weights` - Get only interpolator declustering weights
  * `minneighbors`     - Minimum number of neighbors (default to `1`)
  * `maxneighbors`     - Maximum number of neighbors (default to `10`)
  * `neighborhood`     - Search neighborhood (default to `nothing`)
  * `local_search`     - If rotate/rescale searches using local anisotropies
