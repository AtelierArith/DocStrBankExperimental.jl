```
alphacolor(::Type{<:Colorant})
alphacolor(::Colorant)
```

Return the corresponding transparent color type/instance with storage order (alpha, color).

# Examples

```jldocest; setup = :(using ColorTypes)
julia> alphacolor(RGB)
ARGB

julia> alphacolor(RGBA{Float32})
ARGB

julia> alphacolor(Gray(0.8)) === AGray(0.8, 1.0)
true
```
