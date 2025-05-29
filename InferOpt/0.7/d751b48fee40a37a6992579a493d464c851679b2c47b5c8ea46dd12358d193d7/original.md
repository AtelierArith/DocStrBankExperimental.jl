```julia
shannon_entropy(p::AbstractArray{R<:Real, 1}) -> Any

```

Compute the Shannon entropy of a probability distribution: `H(p) = -∑ pᵢlog(pᵢ)`.
