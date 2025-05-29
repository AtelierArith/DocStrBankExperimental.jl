```
childtype(::Type{T})
childtype(n)
```

Indicates the type of children of the tree node `n` or its type `T`.

If `childtype` can be inferred from the type of the node alone, the type `::Type{T}` definition is preferred (the latter will fall back to it).

**OPTIONAL**: It is strongly recommended to define this wherever possible, as without it almost no tree algorithms can be type-stable.  If `childrentype` is defined and can be known from the node type alone, this function will fall back to `eltype(childrentype(T))`.  If this gives a correct result it's not necessary to define `childtype`.
