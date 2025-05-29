```
shiftathybrids(value::Vector{T} where T<:Real, net::HybridNetwork; checkpreorder::Bool=true)
```

Construct an object [`ShiftNet`](@ref) with shifts on all the edges below hybrid nodes, with values provided. The vector of values must have the same length as the number of hybrids in the network.
