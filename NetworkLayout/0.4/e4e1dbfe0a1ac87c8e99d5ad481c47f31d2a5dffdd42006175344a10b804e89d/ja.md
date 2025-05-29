```
Buchheim(; kwargs...)(adj_matrix)
Buchheim(; kwargs...)(adj_list)
buchheim(adj_matrix; kwargs...)
buchheim(adj_list; kwargs...)
```

Buchheim、Junger、Leipert（2002年、[doi 10.1007/3-540-36151-0*32](https://doi.org/10.1007/3-540-36151-0*32）によって提案されたアルゴリズムを使用しています。

与えられた木の隣接行列またはリスト表現を取り、ノードの座標を返します。

## キーワード引数

  * `Ptype=Float64`: 出力タイプ `Point{2,Ptype}` を決定します。
  * `nodesize=Float64[]`

    各ノードのサイズを決定します。ネットワークのサイズが `nodesize` の長さと一致しない場合は、`ones` で埋めるか、指定されたパラメータを切り捨てます。
