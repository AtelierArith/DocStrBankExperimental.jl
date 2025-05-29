```
subgraph(fg, nodes)
```

与えられたフィーチャーグラフ `fg` からタイプ `FeaturedSubgraph` のサブグラフを返します。グラフ内の `nodes` を予約することによってサブグラフを構築します。

# 引数

  * `fg::AbstractFeaturedGraph`: サブグラフを構築するためのベースフィーチャーグラフ。
  * `nodes::AbstractVector`: `fg` から予約されるノードを指定します。
