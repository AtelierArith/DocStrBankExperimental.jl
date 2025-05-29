```
local_basis_matrix(L::AbstractLat, p::AbsNumFieldOrderIdeal{AbsSimpleNumField, AbsSimpleNumFieldElem}; type = :any) -> MatElem
```

Given a prime ideal `p` and a lattice `L`, return a basis matrix of a lattice `M` such that $M_{p} = L_{p}$. Note that if `p` is an ideal in the base ring of `L`, the completions are taken at the minimum of `p` (which is an ideal in the base ring of the order of `p`).

  * If `type == :submodule`, the lattice `M` will be a sublattice of `L`.
  * If `type == :supermodule`, the lattice `M` will be a superlattice of `L`.
  * If `type == :any`, there may not be any containment relation between `M` and `L`.
