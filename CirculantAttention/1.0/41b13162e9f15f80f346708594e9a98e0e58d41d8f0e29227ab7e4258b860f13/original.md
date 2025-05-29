```
circulant_adjacency(simfun::AbstractSimilarity, x, y, W::Int)
```

Equivalent to `(softmax ∘ circulant_similarity)(simfun, x, y, W)`.

See also [`circulant_similarity`](@ref), [`NNlib.softmax`](@ref).
