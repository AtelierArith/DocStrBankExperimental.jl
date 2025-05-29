Find the longest common subsequence for a vector of sequences.

# Examples

```jldoctest
julia> lcs([1,3,5], [1,2,3])
2-element Vector{Any}:
 1
 3
```

```julia
lcs(v; norm, cf)

```
