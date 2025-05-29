```
eligible_step(start::Floatmu{szE,szf}, stop::Floatmu{szE,szf}) where {szE,szf}
eligible_step(::Type{Floatmu{szE,szf}}, start::Float64, stop::Float64) where {szE,szf}
```

Return the smallest `Floatmu{szE,szf}` eligible step allowed to iterate through the domain `[start,stop]`.

# Examples

```jldoctest
julia> eligible_step(Floatmu{2,2}(-0.5),Floatmu{2,2}(2.5))
0.5
```
