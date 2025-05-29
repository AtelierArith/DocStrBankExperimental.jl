```
Polygon(exterior::AbstractVector{<:Point})
Polygon(exterior::AbstractVector{<:Point}, interiors::Vector{<:AbstractVector{<:Point}})
```

外部点のセットからポリゴンを構築します。内部が指定されている場合、それぞれがポリゴンから切り取られます。
