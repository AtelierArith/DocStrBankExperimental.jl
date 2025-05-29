```
AbstractHPolygon{N} <: AbstractPolygon{N}
```

制約表現における多角形の抽象型。

### 注意事項

このインターフェースの標準実装については、[`HPolygon`](@ref) または [`VPolygon`](@ref) を参照してください。

すべてのサブタイプは、制約が反時計回りにソートされているという不変条件を満たさなければなりません。

すべての具体的な `AbstractHPolygon` は、以下のフィールドを持たなければなりません：

  * `constraints::Vector{HalfSpace{N, AbstractVector{N}}}` – 制約

`AbstractHPolygon` のサブタイプ：

```jldoctest; setup = :(using LazySets: subtypes)
julia> subtypes(AbstractHPolygon)
2-element Vector{Any}:
 HPolygon
 HPolygonOpt
```
