```
cyclicshift(v::AbstractVector, nrow)
```

Return an `eltype(v)` matrix of size `nrow` by `length(v)` with each column consisting of `v` followed by a cyclic shift of `v` followed by ...

```@example
cyclicshift('a':'d', 8)
```
