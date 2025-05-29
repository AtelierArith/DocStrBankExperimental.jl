`complex_reflection_group(STnumber)` or `crg(STnumber)`

`complex_reflection_group(p,q,r)` or `crg(p,q,r)`

The  first form of `complex_reflection_group`  returns the complex reflection group which has Shephard-Todd number `STnumber`, see [Shephard-Todd1954](biblio.htm#ST54).   The   second   form   returns   the imprimitive complex reflection group `G(p,q,r)`.

```julia-repl
julia> G=complex_reflection_group(4)
G₄

julia> degrees(G)
2-element Vector{Int64}:
 4
 6

julia> length(G)
24

julia> W*coxgroup(:A,2) # how to make a non-irreducible group
G₄×A₂

julia> complex_reflection_group(1,1,3) # another way to enter A₂
gl₃

julia> crg(4) # there is also a short alias
G₄
```
