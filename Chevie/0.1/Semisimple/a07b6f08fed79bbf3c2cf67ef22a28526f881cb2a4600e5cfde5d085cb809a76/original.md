`weightinfo(W)`

`W`  is a  Coxeter group  record describing  an algebraic  group `𝐆`, or a `IypeIrred`. The function is independent of the isogeny type of `𝐆`(so just depends  on `refltype(W)`, that is  on the root system).  It returns a dict with the following keys:

  * `:minusculeWeights` the minuscule weights, described as their position  in  the  list  of  fundamental  weights.  For non-irreducible groups, a weight  is the sum of at most one weight in each irreducible component. It  is represented as  the list of  its components. For consistency, in the  case  of  an  irreducible  system,  a  weight  is represented as a one-element list.
  * `:minusculeCoweights` the minuscule coweights, represented in the same manner as the minuscule weights
  * `:decompositions` for each coweight, its decomposition in terms of the generators  of the adjoint fundamental group  (given by the list of the exponents  of the generators). Together with  the next field it enables to work out the group structure of the adjoint fundamental group.
  * `:moduli` the list of orders of the generators of the fundamental group.
  * `:AdjointFundamentalGroup` the list of generators of the adjoint fundamental group, given as permutations of the extended root basis.
  * `:CenterSimplyConnected` A list of semisimple elements generating the center of the universal covering of  𝐆
  * `:chosenAdaptedBasis` A basis  of the  weight lattice  adapted to the root lattice. In the basis of the fundamental weights, the root lattice is  given  by  `C=transpose(cartan(W))`.  The  property  specifying the `:chosenAdaptedBasis` is that the Hermite normal form of `C*chosenAdaptedBasis`  is almost in Smith  normal form (it is diagonal but  the diagonal entries may be  permuted compared to the Smith normal form; the non-trivial entries are in the positions corresponding to the generators of the fundamental group as indicated by `:decompositions`).

```julia-repl
julia> weightinfo(coxgroup(:A,2)*coxgroup(:B,2))
Dict{Symbol, Array} with 8 entries:
  :moduli                  => [3, 2]
  :minusculeWeights        => [[1, 3], [1], [2, 3], [2], [3]]
  :decompositions          => [[2, 1], [2, 0], [1, 1], [1, 0], [0, 1]]
  :highestroot             => [5, 7]
  :chosenAdaptedBasis      => [1 -1 0 0; 0 1 0 0; 0 0 1 0; 0 0 0 1]
  :minusculeCoweights      => [[1, 4], [1], [2, 4], [2], [4]]
  :CenterSimplyConnected   => Vector{Rational{Int64}}[[1//3, 2//3, 0, 0], [0, 0…
  :AdjointFundamentalGroup => [(1,12,2), (4,14)]
```
