```
similar_variable(p::AbstractPolynomialLike, variable::Type{Val{V}})
```

Creates a new variable `V` based upon the the given source polynomial.

```
similar_variable(p::AbstractPolynomialLike, v::Symbol)
```

Creates a new variable based upon the given source polynomial and the given symbol `v`. Note that this can lead to type instabilities.

### Examples

Calling `similar_variable(typedpoly, Val{:x})` on a polynomial created with `TypedPolynomials` results in `TypedPolynomials.Variable{:x}`.
