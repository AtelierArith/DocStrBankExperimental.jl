```julia
struct MultiGraph{T<:Integer} <: WrappedMultiGraphs.AbstractMultiGraph{T<:Integer}
```

  * `graph::Graphs.SimpleGraphs.SimpleGraph`: ラップされたグラフ
