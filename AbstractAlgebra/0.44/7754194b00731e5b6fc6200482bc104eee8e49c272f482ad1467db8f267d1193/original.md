```
map(f, a::MatrixElem{T}) where T <: NCRingElement
```

Transform matrix `a` by applying `f` on each element. This is equivalent to `map_entries(f, a)`.
