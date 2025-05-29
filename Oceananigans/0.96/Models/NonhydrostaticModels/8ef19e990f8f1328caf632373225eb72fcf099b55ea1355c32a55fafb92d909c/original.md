```
BackgroundField(func; parameters=nothing)
```

Returns a `BackgroundField` to be passed to `NonhydrostaticModel` for use as a background velocity or tracer field.

If `parameters` is not provided, `func` must be callable with the signature

```julia
func(x, y, z, t)
```

If `parameters` is provided, `func` must be callable with the signature

```julia
func(x, y, z, t, parameters)
```
