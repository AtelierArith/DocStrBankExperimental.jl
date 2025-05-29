conjugating_elt(b,b₁[,F];ss=Val(:sc))

`b`  and `b₁` should  be elements of  the same Garside  group. The function returns  `a` such that `b^a=b₁` if such exists, and `nothing` otherwise. If an  argument `ss`  is given,  the computation  is done in the corresponding category  –- see [`conjcat`](@ref). If an  argument `F` is given it should be  an automorphism of the braid monoid, like the Frobenius of a reflection coset   attached  to  `b.M.W`;   the  computation  is   then  done  in  the corresponding `F`-conjugacy category.

```julia-repl
julia> W=coxgroup(:D,4)
D₄

julia> B=BraidMonoid(W)
BraidMonoid(D₄)

julia> b=B(2,3,1,2,4,3)
231243

julia> b1=B(1,4,3,2,2,2)
1432.2.2

julia> conjugating_elt(b,b1)
(134312.23)⁻¹

julia> c=conjugating_elt(b,b1;ss=Val(:cyc))
232.2

julia> b^c
1432.2.2

julia> WF=spets(W,Perm(1,2,4))
³D₄

julia> F=Frobenius(WF);

julia> c=B(3,4,3,1,2,3)
343123

julia> conjugating_elt(b,c,F)
124312

julia> ^(b,B(1,2,4,3,1,2),F)
343123
```
