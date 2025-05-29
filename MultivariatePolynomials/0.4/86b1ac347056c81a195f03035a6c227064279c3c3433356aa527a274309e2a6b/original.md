```
nvariables(p::AbstractPolynomialLike)
```

Returns the number of variables in `p`, i.e. `length(variables(p))`. It could be more than the number of variables with nonzero degree (see the Examples section of [`variables`](@ref)).

### Examples

Calling `nvariables(x^2*y)` should return at least 2 and calling `nvariables(x)` should return at least 1.
