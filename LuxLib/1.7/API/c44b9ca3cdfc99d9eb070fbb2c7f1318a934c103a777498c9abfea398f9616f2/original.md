```
bias_activation!!(σ, x, bias)
```

Same as [`bias_activation`](@ref) but might update `x` in-place if possible. Users should not rely on `x` being mutated, it is recommended to use it like `y = bias_activation!!(σ, x, bias)`. If `x` is updated in-place, `y` aliases `x`.

See also [`bias_activation`](@ref), [`fast_activation!!`](@ref).
