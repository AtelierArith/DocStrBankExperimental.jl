```
DistanceSimilarity()
```

`circulant_attention`、`circulant_similarity`、および `circulant_adjacency` で距離類似度の使用を示すために使用されます：

$$
S_{ij} = \frac{1}{2}\mathrm{sum}(\mathrm{abs2}, q[i] - k[j]).
$$

[`DotSimilarity`](@ref) も参照してください。
