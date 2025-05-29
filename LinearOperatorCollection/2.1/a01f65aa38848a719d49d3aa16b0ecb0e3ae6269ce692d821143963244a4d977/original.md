```
NormalOp(T::Type; parent, weights)
```

Lazy normal operator of `parent` with an optional weighting operator `weights.` Computes `adjoint(parent) * weights * parent`.

# Required Argument

  * `T`                        - type of elements, .e.g. `Float64` for `ComplexF32`

# Required Keyword argument

  * `parent`                   - Base operator

# Optional Keyword argument

  * `weights`                  - Optional weights for normal operator. Must already be of form `weights = adjoint.(w) .* w`
