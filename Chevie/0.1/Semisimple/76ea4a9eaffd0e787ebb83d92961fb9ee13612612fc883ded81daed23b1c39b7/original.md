`semisimple_centralizer_representatives(W [,p])` or `sscentralizer_reps`

`W`  should be a Weyl group corresponding  to an algebraic group `𝐆`. This function  returns a list describing representatives  `𝐇` of `𝐆`-orbits of reductive  subgroups  of  `𝐆`  which  are  the  identity component of the centralizer of a semisimple element. Each group `𝐇` is specified by a list `h`   of  reflection  indices  in  `W`   such  that  `𝐇`  corresponds  to `reflection_subgroup(W,h)`.  If a  second argument  `p` is  given, only the list of the centralizers which occur in characteristic `p` is returned.

```julia-repl
julia> W=coxgroup(:G,2)
G₂

julia> sscentralizer_reps(W)
6-element Vector{Vector{Int64}}:
 []
 [1]
 [2]
 [1, 2]
 [1, 5]
 [2, 6]

julia> reflection_subgroup.(Ref(W),sscentralizer_reps(W))
6-element Vector{FiniteCoxeterSubGroup{Perm{Int16},Int64}}:
 G₂₍₎=Φ₁²
 G₂₍₁₎=A₁Φ₁
 G₂₍₂₎=Ã₁Φ₁
 G₂
 G₂₍₁₅₎=A₂
 G₂₍₂₆₎=Ã₁×A₁

julia> sscentralizer_reps(W,2)
5-element Vector{Vector{Int64}}:
 []
 [1]
 [2]
 [1, 2]
 [1, 5]
```
