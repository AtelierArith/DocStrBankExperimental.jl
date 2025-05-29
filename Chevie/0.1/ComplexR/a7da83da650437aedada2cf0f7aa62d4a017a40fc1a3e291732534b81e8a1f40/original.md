`reflections(W)`   a  `Vector{Reflection}`   of  all   reflections  of  the reflection   group   `W`   (including   the   non-distinguished  ones;  see [`Reflection`](@ref)).  `reflections(W)[1:nhyp(W)]`  are  the distinguished reflections.

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
