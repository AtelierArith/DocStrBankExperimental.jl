```
VectorFold{T,V <: AbstractVector{T}}
```

A mutable structure for folded vector that extends the methods of AbstractVector. Compared to `IVectorFold`, this tructure is about 20% faster using iterators. Note that this structure keep an active pointer to the `current` *unfolded* pattern. However, its external behavior is similar to `IVectorFold`.
