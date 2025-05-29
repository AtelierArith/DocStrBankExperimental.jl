`induced_linear_form(W, H, h)`

This routine can be used to find the unipotent class in the reductive group with  Weyl group `W` which contains a  given unipotent class of a reductive subgroup of maximum rank represented by the reflection subgroup `H` of `W`.

The  argument `h` is a linear form on  the roots of `H`, given by its value on  the simple roots; this  linear form is extended  to the roots of `W` by `0`  on the orthogonal of the roots  of `H`; and finally the resulting form is  conjugated by an element of `W` so that it takes positive values on the simple roots. If the initial form describes a Dynkin-Richardson diagram for `H`, the result will describe a Dynkin-Richardson diagram for `W`.

```julia-repl
julia> W=coxgroup(:F,4)
F₄

julia> H=reflection_subgroup(W,[1,3])
F₄₍₁₃₎=A₁×Ã₁Φ₁²

julia> induced_linear_form(W,H,[2,2])
4-element Vector{Int64}:
 0
 1
 0
 0

julia> uc=UnipotentClasses(W);

julia> uc.classes[4].dynkin
4-element Vector{Int64}:
 0
 1
 0
 0

julia> uc.classes[4]
UnipotentClass(A₁+Ã₁)
```

The  example above shows that the class containing the regular class of the Levi subgroup of type `A₁×Ã₁` is the class `A₁+Ã₁`.
