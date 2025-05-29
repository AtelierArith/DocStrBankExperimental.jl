```
polynomial(p::AbstractPolynomialLike)
```

Converts `p` to a value with polynomial type.

```
polynomial(p::AbstractPolynomialLike, ::Type{T}) where T
```

Converts `p` to a value with polynomial type with coefficient type `T`.

```
polynomial(a::AbstractVector, mv::AbstractVector{<:AbstractMonomialLike})
```

Creates a polynomial equal to `dot(a, mv)`.

```
polynomial(terms::AbstractVector{<:AbstractTerm}, s::ListState=MessyState())
```

Creates a polynomial equal to `sum(terms)` where `terms` are guaranteed to be in state `s`.

```
polynomial(f::Function, mv::AbstractVector{<:AbstractMonomialLike})
```

Creates a polynomial equal to `sum(f(i) * mv[i] for i in 1:length(mv))`.

### Examples

Calling `polynomial([2, 4, 1], [x, x^2*y, x*y])` should return $4x^2y + xy + 2x$.
