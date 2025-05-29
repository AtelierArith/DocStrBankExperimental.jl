```
Polygon(points;kwargs...)
```

Return a `Polygon2D` or a `Polygon3D` as appropriate

`points` may be an array of `Vec2`s or `Complex`es, or an $n × 2$ array of `Real`s

# Examples

```julia-repl
julia> Polygon([im,0,1])
Polygon2D(<3 points>)
```
