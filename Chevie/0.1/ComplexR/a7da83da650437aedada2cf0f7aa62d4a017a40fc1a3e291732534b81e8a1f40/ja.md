`reflections(W)` は、反射群 `W` のすべての反射の `Vector{Reflection}` です（非特定のものも含まれます; [`Reflection`](@ref) を参照）。`reflections(W)[1:nhyp(W)]` は特定の反射です。

```julia-repl
julia> W=crg(4)
G₄

julia> reflections(W)
8-element Vector{Reflection{PRG{Cyc{Rational{Int64}}, Int16}}}:
 Reflection(G₄,1,ζ₃)
 Reflection(G₄,2,ζ₃)
 Reflection(G₄,4,ζ₃)
 Reflection(G₄,5,ζ₃)
 Reflection(G₄,1,ζ₃²)
 Reflection(G₄,2,ζ₃²)
 Reflection(G₄,4,ζ₃²)
 Reflection(G₄,5,ζ₃²)
```
