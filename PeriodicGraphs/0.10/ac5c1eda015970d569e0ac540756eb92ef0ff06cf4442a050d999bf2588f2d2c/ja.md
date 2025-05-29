```
isdirectedge(e::PeriodicEdge)
```

`e` が直接である場合は `true` を返します。直接であるとは、`(u, v, ofs)` の形をしており、`u < v` または `u == v && ofs > zero(ofs)` のいずれかを満たすことを意味します。

エッジ `e` が間接であるのは、`reverse(e)` が間接でない場合です。

## 例

```jldoctest
julia> isdirectedge(PeriodicEdge1D(3, 4, (0,)))
true

julia> isdirectedge(PeriodicEdge2D(5, 2, (0,0)))
false

julia> isdirectedge(PeriodicEdge3D(3, 3, (0,-1,2)))
false
```

他にも [`directedge`](@ref) を参照してください。
