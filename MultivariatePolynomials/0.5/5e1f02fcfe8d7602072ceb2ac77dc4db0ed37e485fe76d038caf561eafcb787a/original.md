```
maxdegree(p::Union{AbstractPolynomialLike, AbstractVector{<:AbstractTermLike}})
```

Returns the maximal total degree of the monomials of `p`, i.e. `maximum(degree, terms(p))`.

```
maxdegree(p::Union{AbstractPolynomialLike, AbstractVector{<:AbstractTermLike}}, v::AbstractVariable)
```

Returns the maximal degree of the monomials of `p` in the variable `v`, i.e. `maximum(degree.(terms(p), v))`.

### Examples

Calling `maxdegree` on $4x^2y + xy + 2x$ should return 3, `maxdegree(4x^2y + xy + 2x, x)` should return 2 and  `maxdegree(4x^2y + xy + 2x, y)` should return 1.
