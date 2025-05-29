```
get_vector_graph_colors(graph; reps=100)
```

グラフの色のベクトルを生成します。最初にグラフのためのランダムな貪欲色を生成し（`reps`回繰り返し）、その後各色を分離します。

# 引数

  * `graph`: 色を付けるグラフ。
  * `reps`: ランダムな貪欲色を生成するための繰り返し回数（デフォルトは100）。

# 例

```julia
get_vector_graph_colors(graph) # グラフの色のベクトルを返します
```
