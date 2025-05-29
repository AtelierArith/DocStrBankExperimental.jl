```
u_edge(::Type{T}, src, dst) where T <: Integer -> Edge{T}
u_edge(g::SimpleGraph{T}, src, dst) where T -> Edge{T}
u_edge(mol::AbstractMolGraph{T}, src, dst) where T -> Edge{T}
```

SimpleGraphにまだ実装されていないUndirectedEdgeの回避策
