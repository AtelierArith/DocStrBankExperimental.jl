```
@similar_variable(p::AbstractPolynomialLike, variable)
```

Calls `similar_variable(p, Val{variable})` and binds the result to a variable with the same name.

### Examples

Calling `@similar_variable typedpoly x` on a polynomial created with `TypedPolynomials` binds `TypedPolynomials.Variable{:x}` to the variable `x`.
