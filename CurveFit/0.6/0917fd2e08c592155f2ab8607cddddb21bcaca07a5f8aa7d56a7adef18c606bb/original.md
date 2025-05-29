```
    expsum_fit(x::Union{T,AbstractVector{T}}, y::AbstractVector{T}, n::Int; m::Int = 1, withconst::Bool = true, init::Union{Nothing,ExpSumFitInit} = nothing) where {T <: Real}
```

Fits the sum of `n` exponentials and a constant. 

$$
    y = k + p_1 e^{\lambda_1 t} + p_2 e^{\lambda_2 t} + \ldots + p_n e^{\lambda_n t}
$$

If the keyword `withconst` is set to `false`, the constant is not fitted but set `k=0`.

Uses numerical integration with `m` strips, where the default `m=1` uses linear interpolation. `m=2` and higher require uniform interval and usually lead to better accuracy.

Passing `init` preallocates most needed memory, and can be initialized with [`expsum_init`](@ref).

Returns a `ExpSumFit` struct containing a constant `k` and vectors `p`, `λ`, `τ`, where `τ = -1/λ`.

The algorithm is from [Matlab code of Juan Gonzales Burgos](https://github.com/juangburgos/FitSumExponentials).
