```
KeyedArray(A; i=2:3, j=["a", "b"])
NamedDimsArray(A; i=2:3, j=["a", "b"])
```

These constructors make `KeyedArray(NamedDimsArray(A, names), keys)` or `NamedDimsArray(KeyedArray(A, keys), names)`, which should be equivalent.

These perform less sanity checking than `wrapdims(A; kw...)`.

# Examples

```jldoctest
julia> KeyedArray(reshape(1:12,3,4), row=[:a, :b, :c], iter=10:10:40)
2-dimensional KeyedArray(NamedDimsArray(...)) with keys:
↓   row ∈ 3-element Vector{Symbol}
→   iter ∈ 4-element StepRange{Int64,...}
And data, 3×4 reshape(::UnitRange{Int64}, 3, 4) with eltype Int64:
        (10)  (20)  (30)  (40)
  (:a)     1     4     7    10
  (:b)     2     5     8    11
  (:c)     3     6     9    12

julia> ans[iter=3]
1-dimensional KeyedArray(NamedDimsArray(...)) with keys:
↓   row ∈ 3-element Vector{Symbol}
And data, 3-element Vector{Int64}:
 (:a)  7
 (:b)  8
 (:c)  9
```
