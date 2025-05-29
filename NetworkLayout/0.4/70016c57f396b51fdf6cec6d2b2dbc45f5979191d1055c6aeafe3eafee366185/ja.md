```
Spectral(; kwargs...)(adj_matrix)
spectral(adj_matrix; kwargs...)
```

このアルゴリズムは、スペクトルグラフ描画の技術を使用しています。参考文献はKoren (2003, [doi 10.1007/3-540-45071-8_50](https://doi.org/10.1007/3-540-45071-8_50))を参照してください。

ネットワークの隣接行列表現を取り、ノードの座標を返します。

## キーワード引数

  * `dim=3`, `Ptype=Float64`: 次元と出力タイプ `Point{dim,Ptype}` を決定します。
  * `nodeweights=Float64[]`: 重みのベクトル。ネットワークのサイズが `nodesize` の長さと一致しない場合は、代わりに `ones` を使用してください。
