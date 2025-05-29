```
export_graph(filename, graph::GameGraph)
export_graph(filename, edges::Vector{Vector{Int}})
```

グラフをファイルにエクスポートします。フォーマットは最もシンプルです。行 `n` にはノード `n` からの出力エッジがスペースで区切られてリストされています。
