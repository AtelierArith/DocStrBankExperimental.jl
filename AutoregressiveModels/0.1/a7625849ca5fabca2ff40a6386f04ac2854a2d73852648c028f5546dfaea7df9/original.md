```
impulse(arma::ARMAProcess, nhorz::Integer, ε0::Real=1.0)
```

Same as [`impulse!`](@ref), but allocates an array for storing the results. The number of horizons needs to be specified explicitly with `nhorz`.
