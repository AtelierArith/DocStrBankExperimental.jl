```
function bfs(graph::Graph{T},
             source::T,
             destination::Union{Nothing, T} = nothing) where T
```

ノード `source` から始まる完全な BFS を実行します（オプションで `destination` まで）。

#### 戻り値

  * `::Dict{T, Int}`: BFS パスにおけるノードの距離（キー）。
  * `::Dict{T, T}`: BFS パスにおけるノードの親（キー）。
