```
histvar!(out::AbstractArray{TF,3}, irfs::AbstractArray{TF,3}, shocks::AbstractMatrix)
```

Compute the variance to be used for historical decomposition given impulse response coefficients specified with `irfs` and historical `shocks`. Results are stored in an array `out`. See also [`histvar`](@ref).
