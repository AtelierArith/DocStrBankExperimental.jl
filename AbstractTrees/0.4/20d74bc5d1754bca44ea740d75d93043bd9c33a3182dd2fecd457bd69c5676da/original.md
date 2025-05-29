```
childrentype(::Type{T})
childrentype(n)
```

Indicates the type of the children (the *collection* of children, not individual children) of the tree node `n` or its type `T`.  [`children`](@ref) should return an object of this type.

If the `childrentype` can be inferred from the type of the node alone, the type `::Type{T}` definition is preferred (the latter will fall back to it).

**OPTIONAL**: In most cases, [`childtype`](@ref) is used instead.  If `childtype` is not defined it will fall back to `eltype ∘ childrentype`.
