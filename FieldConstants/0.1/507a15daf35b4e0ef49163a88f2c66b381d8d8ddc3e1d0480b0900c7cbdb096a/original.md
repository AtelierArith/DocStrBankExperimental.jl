```
Constant{N} <: Real
```

Numerical field constant `N` with known value at compile time.

```Julia
julia> Constant(100)
100
```

Operations on `Constant` are closed (`*`, `/`, `+`, `-`, `^`), yet they also behave like `Float64` values when mixed with non-`Constant` arguments.
