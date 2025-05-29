```
upperright{T}(A::AbstractArray{Point{T}})
```

与えられた `A` のすべての点を含む最小の境界矩形（x軸およびy軸に平行な辺を持つ）の右上隅の [`Point`](@ref) を返します。

例:

```jldoctest
julia> upperright([Point(2, 0), Point(1, 1), Point(0, 2), Point(-1, 3)])
2-element Point{Int64} with indices SOneTo(2):
 2
 3
```
