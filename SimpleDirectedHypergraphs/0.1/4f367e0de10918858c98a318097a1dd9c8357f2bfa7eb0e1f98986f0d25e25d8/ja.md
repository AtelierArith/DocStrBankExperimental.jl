```
get_weakly_connected_components(h::H) where {H <: AbstractDirectedHypergraph}
```

有向ハイパーグラフ `h` の弱連結成分の配列（頂点のベクトルの配列）を返します。まず、有向ハイパーグラフを無向ハイパーグラフに変換し、その後にそのハイパーグラフの連結成分を取得します。
