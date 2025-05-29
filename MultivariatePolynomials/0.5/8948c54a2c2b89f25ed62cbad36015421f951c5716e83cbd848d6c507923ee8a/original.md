```
extdegree(p::Union{AbstractPolynomialLike, AbstractVector{<:AbstractPolynomialLike}})
```

Returns the extremal total degrees of the monomials of `p`, i.e. `(mindegree(p), maxdegree(p))`.

```
extdegree(p::Union{AbstractPolynomialLike, AbstractVector{<:AbstractPolynomialLike}}, v::AbstractVariable)
```

Returns the extremal degrees of the monomials of `p` in the variable `v`, i.e. `(mindegree(p, v), maxdegree(p, v))`.

### Examples

Calling `extdegree` on $4x^2y + xy + 2x$ should return `(1, 3)`, `extdegree(4x^2y + xy + 2x, x)` should return `(1, 2)` and  `maxdegree(4x^2y + xy + 2x, y)` should return `(0, 1)`.
