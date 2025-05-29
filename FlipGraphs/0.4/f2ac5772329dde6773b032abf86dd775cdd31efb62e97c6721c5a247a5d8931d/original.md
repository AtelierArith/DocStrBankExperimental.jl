```
twist_edges!(D::DeltaComplex, t::Integer)
twist_edges!(T::TriFace)
```

Twist or untwist all 3 `DualEdges` of a `TriFace`, and reverse the side order.

This action gives an equivalent representation of the same triangulation. It is useful in the case that you would like to untwist a certain edge.

# Examples

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
