```julia
mutable struct MultiDiGraph{T<:Integer} <: WrappedMultiGraphs.AbstractMultiGraph{T<:Integer}
```

  * `graph::Graphs.SimpleGraphs.SimpleDiGraph`: ラップされたグラフ
