```
entropy_dispersion(x; base = 2, kwargs...)
```

Compute the dispersion entropy. This function is just a convenience call to:

```julia
est = Dispersion(kwargs...)
information(Shannon(base), est, x)
```

See [`Dispersion`](@ref) for more info.
