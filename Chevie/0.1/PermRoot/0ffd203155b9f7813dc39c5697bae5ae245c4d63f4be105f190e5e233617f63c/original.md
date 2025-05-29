`refltype(W::ComplexReflectionGroup` or coset`)` or `reflection_type(W)`

returns the `Vector{TypeIrred}` which classifies `W` (see [`TypeIrred`](@ref)).  The  `refltype`  is  used  for displaying `W` at the repl. The function `indices` on the result of `refltype`or on a `TypeIrred` tells  the index in `gens(W)` of each standard generator of the irreducible component  s. In the  REPL display of  `W`, these indices  are omitted when they  are the  expected ones  (the component  is in  order at  the expected indices).

```julia-repl
julia> W=coxgroup(:D,3) # a D₃ is an A₃ in disorder
A₃₍₁₃₂₎

julia> t=refltype(W)
A₃₍₁₃₂₎

julia> indices(t)
3-element Vector{Int64}:
 1
 3
 2
```
