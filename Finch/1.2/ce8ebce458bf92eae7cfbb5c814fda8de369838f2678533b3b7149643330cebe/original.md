```
pattern!(fbr)
```

Return the pattern of `fbr`. That is, return a tensor which is true wherever `fbr` is structurally unequal to its fill_value. May reuse memory and render the original tensor unusable when modified.

```jldoctest
julia> A = Tensor(SparseList(Element(0.0), 10), [2.0, 0.0, 3.0, 0.0, 4.0, 0.0, 5.0, 0.0, 6.0, 0.0])
10 Tensor{SparseListLevel{Int64, Vector{Int64}, Vector{Int64}, ElementLevel{0.0, Float64, Int64, Vector{Float64}}}}:
 2.0
 0.0
 3.0
 0.0
 4.0
 0.0
 5.0
 0.0
 6.0
 0.0

julia> pattern!(A)
10 Tensor{SparseListLevel{Int64, Vector{Int64}, Vector{Int64}, PatternLevel{Int64}}}:
 1
 0
 1
 0
 1
 0
 1
 0
 1
 0
```
