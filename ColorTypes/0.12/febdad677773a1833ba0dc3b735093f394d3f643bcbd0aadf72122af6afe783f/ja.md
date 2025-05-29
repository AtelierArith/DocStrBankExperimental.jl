```
alphacolor(::Type{<:Colorant})
alphacolor(::Colorant)
```

対応する透明色の型/インスタンスをストレージ順序（アルファ、カラー）で返します。

# 例

```jldocest; setup = :(using ColorTypes)
julia> alphacolor(RGB)
ARGB

julia> alphacolor(RGBA{Float32})
ARGB

julia> alphacolor(Gray(0.8)) === AGray(0.8, 1.0)
true
```
