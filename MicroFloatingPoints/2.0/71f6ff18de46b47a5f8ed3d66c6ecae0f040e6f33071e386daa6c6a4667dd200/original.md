```
bias(::Type{Floatmu{szE,szf}}) where {szE, szf}
```

Bias of the exponent for a `Floatmu{szE,szf}`.

# Examples

```jldoctest
julia> bias(Floatmu{8, 23}) 
0x0000007f
```
