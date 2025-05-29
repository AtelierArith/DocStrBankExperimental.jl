```
onehot(vec::AbstractVector) -> Matrix{Float64}
```

Encode a categorical vector to a onehot-encoded matrix. `["Male", "Female", "Others"]` is converted into `[1. 0. 0.; 0. 1. 0.; 0. 0. 1.]`. An index corresponding to a possible value is assigned in the order of first-time appearance in the input vector.
