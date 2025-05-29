```
`HaltonSeq!{T<:AbstractFloat}(H::Vector{T}, B::Int; skip::Int=500)`
```

Copied from an old version of Halton.jl. Replaces `H` with entries from Halton low discrepancy sequence with base `B`. Elements in `H` take values in the interval (0, 1). Keyword argument `skip` is the number initial "burn-in" elements to drop.
