```
AMORS.apply_scaling_factor!(α::Real, x, y) -> α
```

Multiply in-place the entries of `x` by the scalar `α` and the entries of `y` by `inv(α)`. Return `α`. See [`AMORS.scale!`](@ref).
