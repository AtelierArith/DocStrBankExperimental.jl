```
y, A = circulant_attention(simfun::AbstractSimilarity, q, k, v, W::Int)
```

Perform circulant attention on `y=Av`, where A is a row-softmax normalized  circulant-sparse attention matrix (A = rowsoftmax(S)). Each non-zero entry $S_{ij}$ is generated via the similarity function acting on the channel representations of `q` and `k`  at (linearly indexed) pixels `i`, `j` ($S_{ij} = \mathrm{simfun}(q_i, k_j)$). Adjacency matrix $A$ is generated internal and returned as the  second argument. Note: q and k are internally scaled by `sqrt(sqrt(channels))` before being passed to `circulant_adjacency`.

See also [`circulant_adjacency`](@ref), [`circulant_similarity`](@ref), [`DotSimilarity`](@ref), [`DistanceSimilarity`](@ref).
