```
coloralpha(::Type{<:Colorant})
coloralpha(::Colorant)
```

Return the corresponding transparent color type/instance with storage order (color, alpha).

# Examples

```jldocest; setup = :(using ColorTypes)
julia> coloralpha(RGB)
RGBA

julia> coloralpha(ARGB{Float32})
RGBA

julia> coloralpha(Gray(0.8)) === GrayA(0.8, 1.0)
true
```
