```
negative_sample(g::GNNGraph; 
                num_neg_edges = g.num_edges, 
                bidirected = is_bidirected(g))
```

グラフ `g` からランダムな負のエッジ（すなわち非エッジ）をエッジとして含むグラフを返します。

`bidirected=true` の場合、出力グラフは双方向になり、元のグラフからの漏れはありません。

詳細は [`is_bidirected`](@ref) を参照してください。
