```
forecastvar!(out::AbstractArray{T,3}, irfs::AbstractArray{T,3})
```

Compute the variance of forecast error over each horizon given orthogonalized impulse response coefficients specified with `irfs` and store the results in an array `out`. The number of horizons computed is determined by the second dimension of `irfs` and `out` should have the same size as `irfs`. See also [`forecastvar`](@ref).
