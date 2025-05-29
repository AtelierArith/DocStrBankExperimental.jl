```
variables(p::AbstractPolynomialLike)
```

Returns the tuple of the variables of `p` in decreasing order. It could contain variables of zero degree, see the example section.

### Examples

Calling `variables(x^2*y)` should return `(x, y)` and calling `variables(x)` should return `(x,)`. Note that the variables of `m` does not necessarily have nonzero degree. For instance, `variables([x^2*y, y*z][1])` is usually `(x, y, z)` since the two monomials have been promoted to a common type.
