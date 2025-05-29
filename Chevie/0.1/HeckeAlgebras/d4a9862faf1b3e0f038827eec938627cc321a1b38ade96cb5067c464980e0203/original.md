`representation(H::HeckeAlgebra or HeckeCoset,i)`

returns,  for the `i`-th irreducible representation of the Hecke algebra or Hecke  coset `H`, a list  of matrices images of  the generators of `H` in a model of the representation (for Hecke cosets, the result is a `NamedTuple` with fields `gens`, a representation of `hecke(H)`, and `F`, the matrix for the automorphism of `H` in the representation).

This  function  is  based  on  the  classification,  and  is  not yet fully implemented for the Hecke algebras of the groups `G₃₁`, `G₃₂` and `G₃₄`: we have 50 representations out of 59 for type `G₃₁`, 30 representations out of 102  for  type  `G₃₂`  and  38  representations  out of 169 for type `G₃₄`; `nothing` is returned for a missing representation.

```julia-repl
julia> W=crg(24)
G₂₄

julia> H=hecke(W,Pol(:q))
hecke(G₂₄,q)

julia> representation(H,3)
3-element Vector{Matrix{Pol{Cyc{Int64}}}}:
 [q 0 0; -q -1 0; -q 0 -1]
 [-1 0 -1; 0 -1 ((1-√-7)/2)q; 0 0 q]
 [-1 -1 0; 0 q 0; 0 (1+√-7)/2 -1]
```

The  models  implemented  for  imprimitive  types `G(de,e,n)` for `n>2` and `de>1` (this includes Coxeter type `Dₙ`), excepted for `G(2,2,4), G(3,3,3), G(3,3,4), G(3,3,5)` and `G(4,4,3)`, involve rational fractions.

```julia-repl
julia> H=hecke(coxgroup(:D,5),Pol())
hecke(D₅,q)

julia> representation(H,7)
5-element Vector{Matrix{Frac{Pol{Int64}}}}:
 [q 0 0 0; 0 -1 0 0; 0 0 -1 0; 0 0 0 -1]
 [q 0 0 0; 0 -1 0 0; 0 0 -1 0; 0 0 0 -1]
 [1/(-q-1) q/(q+1) 0 0; (q²+q+1)/(q+1) q²/(q+1) 0 0; 0 0 -1 0; 0 0 0 -1]
 [-1 0 0 0; 0 1/(-q²-q-1) (-q²-q)/(-q²-q-1) 0; 0 (q³+q²+q+1)/(q²+q+1) q³/(q²+q+1) 0; 0 0 0 -1]
 [-1 0 0 0; 0 -1 0 0; 0 0 1/(-q³-q²-q-1) (-q³-q²-q)/(-q³-q²-q-1); 0 0 (q⁴+q³+q²+q+1)/(q³+q²+q+1) q⁴/(q³+q²+q+1)]
```
