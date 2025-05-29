```
λ(::Type{Floatmu{szE,szf}})  where {szE,szf}
```

Return λ, the smallest positive *normal* number of the type `Floatmu{szE,szf}`.

# Examples

```jldoctest
julia> λ(Floatmu{2, 2})
1.0

julia> λ(Floatmu{8, 23})==floatmin(Float32)
true
```
