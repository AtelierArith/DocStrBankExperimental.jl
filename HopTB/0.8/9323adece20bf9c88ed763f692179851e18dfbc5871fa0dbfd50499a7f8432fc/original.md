```julia
getdEs(
    tm::AbstractTBModel,
    α::Integer,
    β::Integer,
    k::AbstractVector{<:Real}
) => dEs::Vector{Float64}
```

Calculate d^2 E / dkα dkβ for `tm` at `k`. `α` and `β` are Cartesian directions.

dEs[n] is only correct if n is nondegenerate or completely degenerate.

This function is memoized, which means the arguments and results of the function should never be modified.
