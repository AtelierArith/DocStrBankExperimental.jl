```
AbstractPolygon{N} <: AbstractPolytope{N}
```

凸多角形（すなわち、二次元ポリトープ）のための抽象型です。

### 注意事項

`AbstractPolygon` のサブタイプ（抽象インターフェースを含む）:

```jldoctest; setup = :(using LazySets: subtypes)
julia> subtypes(AbstractPolygon)
2-element Vector{Any}:
 AbstractHPolygon
 VPolygon
```
