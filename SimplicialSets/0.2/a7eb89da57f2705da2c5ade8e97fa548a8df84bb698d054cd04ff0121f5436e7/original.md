```
opposite(x::T) where T <: AbstractSimplex -> OppositeSimplex
opposite(x::T) where {S, T <: OppositeSimplex{S}} -> S
opposite(x::T) where T <: ProductSimplex -> ProductSimplex
```

Return an "interpreted version" of the opposite simplex of `x`:

  * If `x` is already an `OppositeSimplex`, return the underlying simplex.
  * If `x` is a `ProductSimplex`, apply `opposite` to the components and return the corresponding `ProductSimplex`.
  * In all other cases, return `OppositeSimplex(x)`.

See also [`OppositeSimplex`](@ref), [`opposite(::AbstractTensor)`](@ref), [`opposite(::AbstractLinear)`](@ref).
