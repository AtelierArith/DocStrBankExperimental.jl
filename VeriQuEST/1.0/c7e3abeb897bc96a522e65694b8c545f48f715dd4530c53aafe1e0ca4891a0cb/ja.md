```
generate_random_greedy_color(g, reps)
```

この関数はグラフのランダムな貪欲彩色を生成します。Graphsパッケージの`random_greedy_color`関数を使用します。

# 引数

  * `g`: 彩色されるグラフ。
  * `reps`: ランダム貪欲彩色アルゴリズムの繰り返し回数。

# 例

```julia
g = Graphs.grid_graph((5,5))
reps = 10
generate_random_greedy_color(g, reps)
```
