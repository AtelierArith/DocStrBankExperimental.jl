```
AbstractPolynomialZonotope{N} <: LazySet{N}
```

Abstract type for polynomial zonotope sets.

### Notes

See [`DensePolynomialZonotope`](@ref) for a standard implementation of this interface.

Polynomial zonotopes are in general non-convex. They are always bounded.

Every concrete `AbstractPolynomialZonotope` must define the following functions:

  * `center(::AbstractPolynomialZonotope)` – return the center
  * `polynomial_order(::AbstractPolynomialZonotope)` – return the polynomial order
  * `ngens_dep` – return the number of dependent generators
  * `ngens_indep` – return the number of independent generators

The subtypes of `AbstractPolynomialZonotope` (including abstract interfaces):

```jldoctest; setup = :(using LazySets: subtypes)
julia> subtypes(AbstractPolynomialZonotope)
2-element Vector{Any}:
 AbstractSparsePolynomialZonotope
 DensePolynomialZonotope
```
