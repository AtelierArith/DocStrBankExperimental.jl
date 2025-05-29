```julia
struct NestedGraph{T<:Integer, R<:Graphs.AbstractGraph{T<:Integer}, N<:Graphs.AbstractGraph} <: Graphs.AbstractGraph{T<:Integer}
```

  * `flatgr::Graphs.AbstractGraph{T} where T<:Integer`: エッジを持つすべてのサブグラフを組み合わせたフラットグラフビュー
  * `grv::Vector{N} where N<:Graphs.AbstractGraph`: 元のサブグラフ
  * `neds::Array{NestedGraphs.NestedEdge{T}, 1} where T<:Integer`: サブグラフ間のエッジ
  * `vmap::Array{Tuple{T, T}, 1} where T<:Integer`: フラットネットワークのノードを元のグラフ（サブグラフ、ノード）にマッピング

`NestedGraph`は、各頂点が完全グラフである可能性のある頂点のグラフです。接続は`NestedEdge`で行われ、頂点は`NestedVertex`です。NestedGraphsのNestedGraphsも許可されています。
