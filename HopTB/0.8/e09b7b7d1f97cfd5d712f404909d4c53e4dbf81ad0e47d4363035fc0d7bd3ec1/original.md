```julia
getdEs(tm::AbstractTBModel, α::Int64, k::AbstractVector{<:Real})
-->dEs::Vector{Float64}
```

Calculate dE/dk for `tm` at `k` in the `α` direction.

Calculation method is provided in [Wang et al, 2019]. The relevant equation is Eq. (13). Although in that equation, there is no energy different denominator, it is still implicitly assumed that the band is nondegenerate. Therefore, dEs[n] is only correct if n is nondegenerate or completely degenerate.

This function is memoized, which means the arguments and results of the function should never be modified.
