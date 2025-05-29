```julia
struct HyperGraph <: Graphs.AbstractGraph{Int64}
```

ハイパーグラフは、エッジが任意の数の頂点を接続できるグラフの一般化です。

### フィールド

  * `n::Int`: 頂点の数
  * `edges::Vector{Vector{Int}}`: 各ベクトルが対応するインデックスを持つ頂点を接続するハイパーエッジを表す整数のベクトルのベクトル。
