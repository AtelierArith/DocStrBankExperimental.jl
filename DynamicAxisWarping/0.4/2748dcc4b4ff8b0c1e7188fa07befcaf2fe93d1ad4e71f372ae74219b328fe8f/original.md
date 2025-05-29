```
struct SoftDTW{D, T} <: DTWDistance{D}
```

# Arguments:

  * `γ`: smoothing parameter default to 1. Smaller value makes the distance closer to standard DTW.
  * `dist`: Inner distance, defaults to `SqEuclidean()`.
  * `transportcost`
