```
AbstractSparsePolynomialZonotope{N} <: AbstractPolynomialZonotope{N}
```

Abstract type for sparse polynomial zonotope sets.

### Notes

See [`SparsePolynomialZonotope`](@ref) for a standard implementation of this interface.

Every concrete `AbstractSparsePolynomialZonotope` must define the following functions:

  * `expmat(::AbstractSparsePolynomialZonotope)` – return the exponent matrix (sparse PZ only)
  * `genmat_dep(::AbstractSparsePolynomialZonotope)` – return the matrix of dependent generators
  * `genmat_indep(::AbstractSparsePolynomialZonotope)` – return the matrix of independent generators

The subtypes of `AbstractSparsePolynomialZonotope` (including abstract interfaces):

```jldoctest; setup = :(using LazySets: subtypes)
julia> subtypes(AbstractSparsePolynomialZonotope)
2-element Vector{Any}:
 SimpleSparsePolynomialZonotope
 SparsePolynomialZonotope
```
