```
NaNμ(::Type{Floatmu{szE,szf}}) where {szE, szf}
```

NaN in the format `Floatmu{szE,szf}`.

The canonical NaN value has a sign bit set to zero and all bits of the fractional part set to zero except for the leftmost one.

# Examples

```jldoctest
julia> isnan(NaNμ(Floatmu{2, 2}))
true
julia> NaNμ(Floatmu{2, 2})
NaNμ{2, 2}
```
