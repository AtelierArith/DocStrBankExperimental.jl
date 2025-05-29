```
variable(p::AbstractPolynomialLike)
```

Converts `p` to a variable. Throws `InexactError` if it is not possible.

### Examples

Calling `variable(x^2 + x - x^2)` should return the variable `x` and calling `variable(1.0y)` should return the variable `y` however calling `variable(2x)` or `variable(x + y)` should throw `InexactError`.

### Note

This operation is not type stable for the TypedPolynomials implementation if `nvariables(p) > 1` but is type stable for DynamicPolynomials.
