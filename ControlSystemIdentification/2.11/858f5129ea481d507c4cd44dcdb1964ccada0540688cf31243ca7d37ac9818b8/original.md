```
impulseestplot(data,n; σ = 2)
```

Estimates the system impulse response by fitting an `n`:th order FIR model and plots the result with a 95% (2σ) confidence band. Note, the confidence bound is drawn around zero, i.e., it is drawn such that one can determine whether or not the impulse response is significantly different from zero.

This method only supports single-output data, use [`okid`](@ref) for multi-output data.

See also [`impulseest`](@ref) and [`okid`](@ref).
