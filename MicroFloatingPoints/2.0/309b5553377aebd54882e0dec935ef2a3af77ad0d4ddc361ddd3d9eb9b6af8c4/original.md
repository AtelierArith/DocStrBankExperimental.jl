```
μ(::Type{Floatmu{szE,szf}})  where {szE,szf}
```

Return μ, the smallest positive subnormal number of type `Floatmu{szE,szf}`.

# Examples

```jldoctest
julia> μ(Floatmu{2, 2})
0.25
```
