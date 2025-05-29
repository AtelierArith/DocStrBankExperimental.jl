```
chain(vlist::Vector{T}) where {T<:Integer}
```

Create a chain with elements drawn from `vlist`, which must be a permutation of `1:n`. For example, `chain([2,1,3])` returns a poset in which `2 < 1 < 3`.
