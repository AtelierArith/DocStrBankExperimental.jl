```
Polygon(points;kwargs...)
```

適切に `Polygon2D` または `Polygon3D` を返します

`points` は `Vec2` または `Complex` の配列、または $n × 2$ の `Real` の配列である可能性があります

# 例

```julia-repl
julia> Polygon([im,0,1])
Polygon2D(<3 points>)
```
