```julia
get_berry_curvature(tm::AbstractTBModel, α::Int64, β::Int64, k::Vector{<:Real})::Vector{Float64}
```

Calculate Berry curvature Ω for `tm` at `k`.

Ω[n] is only correct if band n is nondegenerate or completely degenerate.
