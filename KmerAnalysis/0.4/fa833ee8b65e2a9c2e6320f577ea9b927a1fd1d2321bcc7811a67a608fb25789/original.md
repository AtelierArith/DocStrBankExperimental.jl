```
merge_into!(a::Vector{MerCount{M}}, b::Vector{MerCount{M}}) where {M<:AbstractMer}
```

Merge the `MerCount`s from vector `b` into the vector `a`.

!!! note
    This will sort the input vectors `a` and `b`.

