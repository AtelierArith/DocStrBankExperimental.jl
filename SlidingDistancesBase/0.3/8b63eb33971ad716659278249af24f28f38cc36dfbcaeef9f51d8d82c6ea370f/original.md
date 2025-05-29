```julia
distance_profile!(D, _, QT, μA, σA, μT, σT, m, i)

```

Accepts precomputed sliding mean and std of the input arrays. `QT` is the windowed dot product and `i` is the index into `T` (the longer time series).
