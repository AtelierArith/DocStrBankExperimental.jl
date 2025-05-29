```
fit!(f::Factor; maxiter::Integer=10000, tol::Real=1e-8)
```

Reestimate the factor model with data contained in `f`. This method assumes that the content in `f` remains valid after any modification and allows non-allocating estimation. See also [`Factor`](@ref) and [`fit`](@ref).
