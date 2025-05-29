```julia
struct AliasingScalarSampler
```

Sampler from intensity map given Euclidean domain `x` and probability weights `p_x`.

Example

`AliasingScalarSampler(x::Vector{<:Real}, p_x::Vector{<:Real}; SNRfloor::Float64=0.0)`
