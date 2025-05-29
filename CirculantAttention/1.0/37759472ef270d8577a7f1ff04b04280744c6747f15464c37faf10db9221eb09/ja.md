```
y, A = circulant_attention(simfun::AbstractSimilarity, q, k, v, W::Int)
```

`y=Av`に対して循環アテンションを実行します。ここで、Aは行ソフトマックス正規化された循環スパースアテンション行列です（A = rowsoftmax(S)）。各非ゼロエントリ$S_{ij}$は、(線形インデックス)ピクセル`i`、`j`における`q`と`k`のチャネル表現に作用する類似性関数によって生成されます（$S_{ij} = \mathrm{simfun}(q_i, k_j)$）。隣接行列$A$は内部で生成され、2番目の引数として返されます。注意: `q`と`k`は、`circulant_adjacency`に渡される前に`sqrt(sqrt(channels))`で内部的にスケーリングされます。

[`circulant_adjacency`](@ref)、[`circulant_similarity`](@ref)、[`DotSimilarity`](@ref)、[`DistanceSimilarity`](@ref)も参照してください。
