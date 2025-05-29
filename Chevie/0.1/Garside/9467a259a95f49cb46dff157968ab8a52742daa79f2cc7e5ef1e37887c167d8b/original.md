`centralizer_gens(b[,F];ss=Val(:sc))`

a  list of generators of the centralizer of `b`. The computation is done by computing  the  endomorphisms  of  the  object  `b`  in the category of its sliding  circuits. If an argument `ss` is given, the computation is done in the corresponding category –- see [`conjcat`](@ref).

If  an argument  `F` is  given it  should be  an automorphism  of the braid monoid,  like the Frobenius of a reflection coset attached to `b.M.W`; then the `F`-centralizer is computed.

```julia-repl
julia> W=coxgroup(:D,4)
D₄

julia> B=BraidMonoid(W)
BraidMonoid(D₄)

julia> w=B(4,4,4)
4.4.4

julia> cc=centralizer_gens(w)
8-element Vector{GarsideElt{Perm{Int16}, BraidMonoid{Perm{Int16}, FiniteCoxeterGroup{Perm{Int16},Int64}}}}:
 1
 (31432)⁻¹231432
 (1)⁻¹34.431
 (2)⁻¹34.432
 (32431)⁻¹132431
 4
 34.43
 2

julia> shrink(cc)
5-element Vector{GarsideElt{Perm{Int16}, BraidMonoid{Perm{Int16}, FiniteCoxeterGroup{Perm{Int16},Int64}}}}:
 4
 2
 1
 34.43
 (3243)⁻¹13243

julia> centralizer_gens(w;ss=Val(:cyc))
1-element Vector{GarsideElt{Perm{Int16}, BraidMonoid{Perm{Int16}, FiniteCoxeterGroup{Perm{Int16},Int64}}}}:
 4

julia> F=Frobenius(spets(W,Perm(1,2,4)));

julia> centralizer_gens(w,F)
2-element Vector{GarsideElt{Perm{Int16}, BraidMonoid{Perm{Int16}, FiniteCoxeterGroup{Perm{Int16},Int64}}}}:
 124
 312343123
```
