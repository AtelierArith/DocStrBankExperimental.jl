```
coloralpha(::Type{<:Colorant})
coloralpha(::Colorant)
```

対応する透明色の型/インスタンスを、ストレージ順序（色、アルファ）で返します。

# 例

```jldocest; setup = :(using ColorTypes)
julia> coloralpha(RGB)
RGBA

julia> coloralpha(ARGB{Float32})
RGBA

julia> coloralpha(Gray(0.8)) === GrayA(0.8, 1.0)
true
```
