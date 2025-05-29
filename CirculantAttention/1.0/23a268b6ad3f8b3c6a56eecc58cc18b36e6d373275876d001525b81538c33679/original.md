```
circulant_similarity(simfun::AbstractSimilarity, x, y, W::Int)
```

Returns Circulant matrix with circulant-sparse data. Each non-zero `S[i,j,b]` is  populated by `simfun` evaluated at the linearized pixel locations of `x` and `y`,  i.e. `S[i,j,b] = simfun(x[...,i,b], y[...,j,b], W)` for max(i⃗, j⃗) ≤ W. The non-zero entrie  locations are determined by the windowsize `W` and number of spatial dimensions in `x` and `y`.

See also [`DotSimilarity`](@ref), [`DistanceSimilarity`](@ref).
