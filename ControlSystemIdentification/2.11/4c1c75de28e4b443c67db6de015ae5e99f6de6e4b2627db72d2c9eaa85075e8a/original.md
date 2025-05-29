```
ir, t, Σ = impulseest(d::AbstractIdData, n; λ=0, estimator=ls)
```

Estimates the system impulse response by fitting an `n`:th order FIR model. Returns impulse-response estimate, time vector and covariance matrix.

This function only supports single-output data, use [`okid`](@ref) for multi-output data.

See also [`impulseestplot`](@ref) and [`okid`](@ref).
