```
jacobian(fdm, f, x...)
```

Approximate the Jacobian of `f` at `x` using `fdm`. Results will be returned as a `Matrix{<:Real}` of `size(length(y_vec), length(x_vec))` where `x_vec` is the flattened version of `x`, and `y_vec` the flattened version of `f(x...)`. Flattening performed by [`to_vec`](@ref).
