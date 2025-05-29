```julia
plugin_bandwidth(
    x::AbstractArray{T<:Real, 1},
    y::AbstractArray{T<:Real, 1};
    ν,
    p,
    kernel,
    W
) -> Any

```

Estimate the rule-of-thumb plugin bandwidth.
