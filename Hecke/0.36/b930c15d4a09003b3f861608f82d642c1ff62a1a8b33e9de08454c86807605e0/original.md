```
gens(A::GroupAlgebra, return_full_basis::Val = Val(false))
  -> Vector{GroupAlgebraElem}
```

Returns a subset of `basis(A)`, which generates $A$ as an algebra over `base_ring(A)`. If `return_full_basis` is set to `Val(true)`, the function also returns a `Vector{AbstractAssociativeAlgebraElem}` containing a full basis consisting of monomials in the generators and a `Vector{Vector{Tuple{Int, Int}}}` containing the information on how these monomials are built. E. g.: If the function returns `g`, `full_basis` and `v`, then we have `full_basis[i] = prod( g[j]^k for (j, k) in v[i] )`.
