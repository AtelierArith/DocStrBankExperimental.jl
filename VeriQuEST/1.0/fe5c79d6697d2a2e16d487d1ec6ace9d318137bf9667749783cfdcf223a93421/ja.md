```
separate_each_color(g::Graphs.Coloring{Int64})
```

この関数は `Graphs.Coloring{Int64}` から抽出し、`Vector{Vector{Int64}}` を返します。色付けが選択されると、次のような整数のベクトルが得られます：

  * 1 はダミー頂点を表します
  * 2 はトラップを表します

# 引数

  * `g::Graphs.Coloring{Int64}`: グラフの色付けオブジェクト。

# 例

`julia g = Graphs.grid_graph((5,5)) coloring = Graphs.greedy_color(g) separate_each_color(coloring)`
