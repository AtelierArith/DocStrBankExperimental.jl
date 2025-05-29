```
AbstractPolyhedron{N} <: ConvexSet{N}
```

閉じた凸多面体集合のための抽象型です。

### 注意事項

このインターフェースの標準実装については、[`HPolyhedron`](@ref)を参照してください。

具体的な`AbstractPolyhedron`は、以下の関数を定義する必要があります：

  * `constraints_list(::AbstractPolyhedron)` – すべての面の制約のリストを返します

多面体は有限数の閉じた半空間の交差として定義されます。そのため、多面体は閉じていて凸ですが、必ずしも有界ではありません。有界な多面体は*多面体*と呼ばれます（[`AbstractPolytope`](@ref）を参照）。

`AbstractPolyhedron`のサブタイプ（抽象インターフェースを含む）：

```jldoctest; setup = :(using LazySets: subtypes)
julia> subtypes(AbstractPolyhedron)
8-element Vector{Any}:
 AbstractPolytope
 HPolyhedron
 HalfSpace
 Hyperplane
 Line
 Line2D
 Star
 Universe
```
