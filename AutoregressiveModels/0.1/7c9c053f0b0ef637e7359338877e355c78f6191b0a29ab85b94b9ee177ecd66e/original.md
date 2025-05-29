```
impulse!(out::AbstractArray, arma::ARMAProcess, ε0::Real=1.0)
```

Compute the responses of the `arma` process to the impulse specified with `ε0` and store the results in `out`. The number of horizons to be computed is determined by the length of `out`. See also [`impulse`](@ref) and [`simulate!`](@ref).
