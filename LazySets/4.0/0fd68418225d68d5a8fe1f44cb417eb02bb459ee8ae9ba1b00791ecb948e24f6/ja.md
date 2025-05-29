```
AbstractPolytope{N} <: AbstractPolyhedron{N}
```

コンパクトな凸多面体集合のための抽象型。

### ノート

このインターフェースの標準実装については、[`HPolytope`](@ref) または [`VPolytope`](@ref) を参照してください。

すべての具体的な `AbstractPolytope` は、次のメソッドを定義する必要があります：

  * `vertices_list(::AbstractPolytope)` – すべての頂点のリストを返す

```jldoctest; setup = :(using LazySets: subtypes)
julia> subtypes(AbstractPolytope)
5-element Vector{Any}:
 AbstractCentrallySymmetricPolytope
 AbstractPolygon
 HPolytope
 Tetrahedron
 VPolytope
```

多面体は有界な多面体です（[`AbstractPolyhedron`](@ref) を参照）。多面体は、次のいずれかの同値な性質を持つコンパクトな凸集合です：

1. 有限個の閉じた半空間の交差である。
2. 有限個の頂点の凸包である。
