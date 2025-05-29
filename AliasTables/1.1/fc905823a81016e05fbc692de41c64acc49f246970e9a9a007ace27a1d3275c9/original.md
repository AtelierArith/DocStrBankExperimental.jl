```
probabilities(float, at::AliasTable{T}) -> Vector{<:AbstractFloat}
```

Return the sampling probabilities of `at`. The returned vector will sum to 1.0, up to rounding error.

# Example

```jldoctest
julia> AliasTables.probabilities(float, AliasTable([1, 3, 1]))
3-element Vector{Float64}:
 0.2
 0.6
 0.2
```
