```julia
MMAPModel(
    vars::AbstractArray{LT, 1},
    cards::AbstractVector{Int64},
    factors::Array{<:TensorInference.Factor{T}, 1};
    queryvars,
    openvars,
    evidence,
    optimizer,
    simplifier,
    marginalize_optimizer,
    marginalize_simplifier
)

```
