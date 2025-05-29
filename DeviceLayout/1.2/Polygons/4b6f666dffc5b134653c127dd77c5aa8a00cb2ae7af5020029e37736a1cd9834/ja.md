```
struct Polygon{T} <: AbstractPolygon{T}
    p::Vector{Point{T}}
    Polygon(x) = new(x)
    Polygon(x::AbstractPolygon) = convert(Polygon{T}, x)
end
```

座標のリストによって定義されたポリゴン。最初の点は最後に繰り返されるべきではありません（ただし、これはGDS形式に対しては真です）。
