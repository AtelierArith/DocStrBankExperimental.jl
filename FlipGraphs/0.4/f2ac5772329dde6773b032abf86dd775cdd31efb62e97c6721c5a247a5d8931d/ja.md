```
twist_edges!(D::DeltaComplex, t::Integer)
twist_edges!(T::TriFace)
```

`TriFace`のすべての3つの`DualEdges`をひねるか、または元に戻し、側面の順序を逆にします。

このアクションは、同じ三角形分割の同等の表現を提供します。特定のエッジを元に戻したい場合に便利です。

# 例

```julia-repl
julia> D = deltacomplex([1,2,-1,2]);
julia> T = get_vertex(D,1);
julia> edges(T)
3-element Array{DualEdge,1}:
 DualEdge 2 : (Δ1)-(1)-------(2)-(Δ2)
 DualEdge 1 : (Δ1)-(2)-------(3)-(Δ2)
 DualEdge 3 : (Δ2)-(1)---↺---(3)-(Δ1)
 julia> twist_edges!(T);
 julia> edges(T)
 3-element Array{DualEdge,1}:
 DualEdge 3 : (Δ2)-(1)-------(1)-(Δ1)
 DualEdge 1 : (Δ1)-(2)---↺---(3)-(Δ2)
 DualEdge 2 : (Δ1)-(3)---↺---(2)-(Δ2)
```
