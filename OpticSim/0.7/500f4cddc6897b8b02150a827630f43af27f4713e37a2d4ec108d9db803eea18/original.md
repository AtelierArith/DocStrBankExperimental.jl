```
uvrange(s::ParametricSurface)
uvrange(::Type{S}) where {S<:ParametricSurface}
```

Returns a tuple of the form: `((umin, umax), (vmin, vmax))` specifying the limits of the parameterisation for this surface type. Also implemented for some `Surface`s which are not `ParametricSurface`s (e.g. `Rectangle`).
