`char_values(H::HeckeAlgebra,v::Vector{<:Integer})`

For an Iwahori-Hecke algebra this computes the character values of `H` on the `Tbasis(H)(v)`.

For  `H` the Hecke algebra  of a complex reflection  group `W` this routine computes  character values on a  lift of the element  of `W` defined by the word `v` in `gens(W)`.

For  complex reflection  groups the  character table  of the  generic Hecke algebra  of  `W`  has  been  computed  (not  entirely for 3 exceptions, see `representation`)  in the  sense that,  if `s₁,…,sₙ`  are generators of the braid  group lifting  the Broué-Malle-Rouquier-Bessis-Michel  generators of `W`,  there is at least one element `v`  in each conjugacy class of `W` and one  expression in the generators for it  such that the character values of the  image `Tᵥ`  in the  Hecke algebra  of the  lift to the braid group are known.  Such an expression in the generators  will be called a *known* word (the  list of known words  is obtained by `word.(conjugacy_classes(W))`. If the  word `v` is known, the computation is quick using the character table. If  not,  the  function  computes  the  trace  of  `Tᵥ` in each irreducible representation.   The   values   returned   are   `missing`  for  missing representations (see `representation`).

```julia-repl
julia> W=crg(4)
G₄

julia> H=hecke(W,Pol(:q))
hecke(G₄,q)

julia> char_values(H,[2,1,2])
7-element Vector{Pol{Cyc{Int64}}}:
 q³
 1
 1
 0
 0
 0
 -q
```
