```
mindegree(p::Union{AbstractPolynomialLike, AbstractVector{<:AbstractPolynomialLike}})
```

Returns the minimal total degree of the monomials of `p`, i.e. `minimum(degree, terms(p))`.

```
mindegree(p::Union{AbstractPolynomialLike, AbstractVector{<:AbstractPolynomialLike}}, v::AbstractVariable)
```

Returns the minimal degree of the monomials of `p` in the variable `v`, i.e. `minimum(degree.(terms(p), v))`.

### Examples

Calling `mindegree` on on $4x^2y + xy + 2x$ should return 1, `mindegree(4x^2y + xy + 2x, x)` should return 1 and  `mindegree(4x^2y + xy + 2x, y)` should return 0.
