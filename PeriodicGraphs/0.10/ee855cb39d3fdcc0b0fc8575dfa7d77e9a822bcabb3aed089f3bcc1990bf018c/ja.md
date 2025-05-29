```
directedge(e::PeriodicEdge{D}) where D
directedge(src::PeriodicVertex{D}, dst::PeriodicVertex{D}) where D
directedge(src, dst, ofs::Union{SVector{D,T},NTuple{D,T}}) where {D,T}
```

`e = PeriodicEdge{D}(src, dst)` に対応する直接エッジを返します。すなわち、`e` が直接であれば `e` 自身を返し、そうでなければ `reverse(e)` を返します。

## 例

```jldoctest
julia> directedge(PeriodicEdge1D(3, 4, (0,)))
PeriodicEdge1D(3, 4, (0,))

julia> directedge(PeriodicEdge2D(5, 2, (0,0)))
PeriodicEdge2D(2, 5, (0,0))

julia> directedge(PeriodicEdge3D(3, 3, (0,-1,2)))
PeriodicEdge3D(3, 3, (0,1,-2))
```

[`isdirectedge`](@ref) も参照してください。
