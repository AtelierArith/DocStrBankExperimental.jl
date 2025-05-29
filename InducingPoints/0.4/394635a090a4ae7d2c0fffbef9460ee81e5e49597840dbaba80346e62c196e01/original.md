```
UniformGrid{T,Titer} <: AbstractVector{T}
```

A memory-efficient custom object representing a wrapper around a `Iterators.ProductIterator`. Supports broadcasting and other relevant array methods, and avoids explicitly computing all points on the grid.  
