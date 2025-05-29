```
y, A = circulant_mh_attention(simfun::AbstractSimilarity, q, k, v, W::Int, nheads::Int)
```

Performs circulant multi-head attention, i.e., performing circulant attetion of `nheads`-groups separately and concatenating the result along channels. The number of channels in `q`, `k`, `v` must be divisible by `nheads`. The returned adjacency matrix `A` will have `size(A, 3) == nheads`.

See also [`circulant_attention`](@ref), [`DotSimilarity`](@ref), [`DistanceSimilarity`](@ref).
