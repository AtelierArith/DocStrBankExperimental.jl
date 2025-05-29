`degrees(W::ComplexReflectionGroup)`

returns  a list  holding the  degrees of  `W` as  a reflection group on the vector  space `V` on which  it acts. These are  the degrees `d₁,…,dₙ` where `n`  is the dimension of  `V` of the basic  invariants of `W` in `SV`. They reflect  various properties  of `W`;  in particular,  their product  is the cardinality of `W`.

```julia-repl
julia> W=complex_reflection_group(30)
H₄

julia> degrees(W)
4-element Vector{Int64}:
  2
 12
 20
 30

julia> length(W)
14400
```
