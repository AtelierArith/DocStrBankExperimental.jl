`reduced(H::CoxeterGroup,W::CoxeterGroup,i=nref(W))`

The  elements `w∈ W` which are `H`-reduced, and of length `≤i` (by default all of them), grouped by length.

```julia-repl
julia> W=coxgroup(:G,2)
G₂

julia> H=reflection_subgroup(W,[2,6])
G₂₍₂₆₎=Ã₁×A₁

julia> [word(W,w) for S in reduced(H,W) for w in S]
3-element Vector{Vector{Int64}}:
 []
 [1]
 [1, 2]
```
