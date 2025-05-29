```
extent(a::Array{T, N})
extent(data::Dict)
extent(a::Extent2D, b::Extent2D)
extent(a::Extent, b::Extent)
```

数学的ベクトルや粒子の配列、または二つの `Extent` を比較することによって、さらには `Extent` の配列によって `Extent` を取得します。

## 例

```jl
julia> extent([Ball(PVector(-1.0u"m", 1.0u"m", 1.0u"m"), PVector(u"m/s"), PVector(u"m/s^2"), 1.0u"kg", 1),
               Ball(PVector(1.0u"m", -1.0u"m", -1.0u"m"), PVector(u"m/s"), PVector(u"m/s^2"), 1000.0u"g", 2)])
Extent: xMin = -1.0 m, xMax = 1.0 m, yMin = -1.0 m, yMax = 1.0 m, zMin = -1.0 m, zMax = 1.0 m, SideLength = 2.0 m, Center = PVector(0.0 m, 0.0 m, 0.0 m)
```
