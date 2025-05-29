`fundamental_group(W)`

This  function returns the fundamental group of the algebraic group defined by  the Coxeter  group struct  `W`. This  group is  returned as  a group of diagram  automorphisms  of  the  corresponding  affine Weyl group, which is represented  as a group of permutations of the set of simple roots enriched by the lowest root of each irreducible component. The definition we take of the  fundamental group of a (not necessarily semisimple) reductive group is (P∩ Y(𝐓))/Q where P is the coweight lattice (the dual lattice in Y(𝐓)⊗ ℚ of the  root  lattice)  and  Q  is  the  coroot  latice. The bijection between elements  of P/Q and  diagram automorphisms is  explained in the context of non-irreducible groups for example in [§3.B Bonnafé2005](biblio.htm#Bon05).

```julia-repl
julia> W=coxgroup(:A,3) # the adjoint group
A₃

julia> fundamental_group(W) # the 12th root is the lowest one
Group((1,12,3,2))

julia> W=rootdatum(:sl,4) # the semisimple simply connected group
sl₄

julia> fundamental_group(W)
Group(Perm{Int16}[])
```
