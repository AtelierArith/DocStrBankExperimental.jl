```
logdensityof(object, x)::Real
```

Compute the logarithmic value of the density `object` (resp. its associated density) at a given point `x`.

```jldoctest a
julia> DensityKind(object)
IsDensity()

julia> logy = logdensityof(object, x); logy isa Real
true
```

See also [`DensityKind`](@ref) and [`densityof`](@ref).
