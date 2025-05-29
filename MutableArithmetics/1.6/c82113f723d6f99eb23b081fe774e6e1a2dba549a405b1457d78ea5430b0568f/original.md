```
mutable_copy(x)
```

Return a copy of `x` that can be mutated with MultableArithmetics's API without altering `x`.

## Examples

The copy of a JuMP affine expression does not copy the underlying model as it cannot be modified though the MultableArithmetics's API, however, it calls [`copy_if_mutable`](@ref) on the coefficients and on the constant as they could be mutated.
