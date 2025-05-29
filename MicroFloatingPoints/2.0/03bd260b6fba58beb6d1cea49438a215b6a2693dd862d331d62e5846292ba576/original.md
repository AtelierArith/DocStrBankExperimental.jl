```
Emin(::Type{Floatmu{szE,szf}}) where {szE, szf}
```

Minimum unbiased exponent for a `Floatmu{szE,szf}` returned as an `Int32`.

See: `exponent_max`, `exponent_raw_max`, [`Emax`](@ref)

# Examples

```jldoctest
julia> Emin(Floatmu{8, 23})
-126
```
