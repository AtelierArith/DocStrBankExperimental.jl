```
densityof(object, x)::Real
```

Compute the value of the density `object` (resp. its associated density) at a given point `x`.

```jldoctest a
julia> DensityKind(object)
IsDensity()

julia> densityof(object, x) == exp(logdensityof(object, x))
true
```

`densityof(object, x)` defaults to `exp(logdensityof(object, x))`, but may be specialized.

See also [`DensityKind`](@ref) and [`densityof`](@ref).
