```
DistanceSimilarity()
```

Used in `circulant_attention`, `circulant_similarity`, and `circulant_adjacency` to indicate use of distance similarity:

$S_{ij} = \frac{1}{2}\mathrm{sum}(\mathrm{abs2}, q[i] - k[j]).$

See also [`DotSimilarity`](@ref).
