```
netgraphplot(ng::NetsedGraph)
netgraphplot!(ax, ng::NetsedGraph)
```

`NestedGraph`として表現されたngのグラフプロットを作成します。

## 属性

  * `show_routers = false`: ノードのラベルを表示する
  * `show_links = false`: リンクのラベルを表示する
  * `color_paths = nothing`: 指定されたパスに色を付ける

各ネストされた`Vector`がパスである`Vector{Vector{Integer}}`を渡す必要があります。各パスは異なる色で着色されます。

  * `color_edges = nothing`: 指定されたエッジに色を付ける

`Vector{Vector{Edge}}`を渡します。各ネストされた`Vector{Edge}`は異なる色を取得します。

  * `pure_colors = nothing`: エッジ/パスに使用する色の`Vector`を入力します。
  * `circle_nodes = nothing`: 円を描くノードを選択します。

`Vector{Vector{Int}}`を渡します。各ネストされた`Vector{Int}`は同じ色を取得します。
