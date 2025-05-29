`torus_order(W::ComplexReflectionGroup,i,q=Pol())`

returns  as a  polynomial in  `q` the  toric order  of the `i`-th conjugacy class  of `W`. This is the characteristic  polynomial of an element of that class  on  the  reflection  representation  of  `W`.  It is the same as the generic  order of the reflection subcoset `torus(W,i)` of `W` determined by the trivial subgroup and a representative of the `i`-th conjugacy class.

```julia-repr
julia> W=complex_reflection_group(4)

julia> torus_order.(Ref(W),1:nconjugacy_classes(W),Pol(:q))
7-element Vector{Pol{Cyc{Int64}}}:
 q²-2q+1
 q²+2q+1
 q²+1
 q²-ζ₃q+ζ₃²
 q²+ζ₃q+ζ₃²
 q²+ζ₃²q+ζ₃
 q²-ζ₃²q+ζ₃
```
