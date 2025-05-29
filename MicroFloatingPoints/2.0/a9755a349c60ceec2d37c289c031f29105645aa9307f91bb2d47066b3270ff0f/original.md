```
Emax(::Type{Floatmu{szE,szf}}) where {szE, szf}
```

Maximum unbiased exponent for a `Floatmu{szE,szf}` returned as an `UInt32`.

See: `exponent_max`, `exponent_raw_max`, [`Emin`](@ref)

# Examples

```jldoctest
julia> Emax(Floatmu{8, 23})
0x0000007f
```
