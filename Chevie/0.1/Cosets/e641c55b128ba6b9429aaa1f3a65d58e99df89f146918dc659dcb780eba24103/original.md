`spets(W::ComplexReflectionGroup, F::Matrix=I(rank(W)))`

This  function returns a or  a `CoxeterCoset` or a  `Spets`. `F` must be an invertible  matrix, representing an automorphism of the vector space `V` of dimension  of dimension `rank(W)` which for  a finite Coxeter group induces an  automorphism of the root  system of `parent(W)`, or  for a more general complex reflection group just stabilizes `W`.

The returned struct has in particular the following fields:

`.W`: the group `W`

`.F`: the matrix acting on `V` which represents the unique element `phi` in `WF` which preserves the positive roots (for finite Coxeter groups) or some "canonical" representative of the coset for more general complex reflection groups.

`.phi`:  a `Perm`, the permutation of the roots of `W` induced by `.F` (for general  complex reflection groups this may be a permutation up to scalars) (also  for Coxeter groups the element of smallest length in the NormalCoset `W .phi`).

In the first example we create a Coxeter coset corresponding to the general unitary group `GU_3(q)` over the finite field `FF(q)`.

```julia-repl
julia> W=rootdatum(:gl,3)
gl₃

julia> gu3=spets(W,-reflrep(W,W()))
²A₂Φ₂

julia> F4=coxgroup(:F,4);D4=reflection_subgroup(F4,[1,2,16,48])
F₄₍₁‚₂‚₉‚₁₆₎=D₄₍₃₂₁₄₎

julia> spets(D4,[1 0 0 0;0 1 2 0;0 0 0 1;0 0 -1 -1])
F₄₍₉‚₁₆‚₁‚₂₎=³D₄₍₃₄₁₂₎
```

`spets(W::ComplexReflectionGroup,p::Perm)`

In  this version `F` is  defined by the permutation  of the simple roots it does.

```julia-repl
julia> W=coxgroup(:A,3)
A₃

julia> spets(W,Perm(1,3))
²A₃
```
