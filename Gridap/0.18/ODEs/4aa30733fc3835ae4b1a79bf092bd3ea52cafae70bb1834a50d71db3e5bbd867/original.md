```
∂t(f::DerivableType, ::Val{k}) -> DerivableType
```

Build the `k`-th-order time derivative operator for `f`.

Alias for `time_derivative(f, Val(k))`.
