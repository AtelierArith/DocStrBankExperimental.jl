```
detecthlinearity(hr::HRepresentation, solver; kws...)
```

Return a new H-representation with linearity detected using `solver`.

The remaining keyword arguments `kws` are passed to [`detect_new_linearities`](@ref).
