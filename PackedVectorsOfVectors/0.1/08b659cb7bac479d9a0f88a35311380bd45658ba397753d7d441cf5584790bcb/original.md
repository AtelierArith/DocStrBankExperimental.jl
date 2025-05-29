```
packed_indices(n) -> pv::PackedVectorOfVectors
```

Packed vector of vectors such that the `k`th nested vector has length `nth(n,k)` and `pv[k][i]` is the index in the flattened vector of the `i`th element in the `k`th nested vector.

# Examples

```jldoctest
julia> packed_indices([2,3])
2-element pack(::Vector{Vector{Int64}}):
 1:2
 3:5
```
