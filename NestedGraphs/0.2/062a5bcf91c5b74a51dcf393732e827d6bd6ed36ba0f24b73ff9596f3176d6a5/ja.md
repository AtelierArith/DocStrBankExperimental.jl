```julia
struct NestedEdge{T<:Integer} <: Graphs.SimpleGraphs.AbstractSimpleEdge{T<:Integer}
```

  * `src::Tuple{T, T} where T<:Integer`
  * `dst::Tuple{T, T} where T<:Integer`

`NestedEdge`は`NestedGraph`内のグラフを接続するか、単に`NestedGraph`内のノードを接続します。`NestedEdge`は2つの`NestedVertex`を接続します。これは、すべての`NestedEdge`が特定のノードに接続し、全体のサブグラフグラフに対してハイパーエッジとして接続されないことを意味します。
