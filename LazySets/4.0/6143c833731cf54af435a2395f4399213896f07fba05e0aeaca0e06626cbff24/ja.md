```
AbstractCentrallySymmetric{N} <: ConvexSet{N}
```

中心対称コンパクト凸集合のための抽象型。

### ノート

すべての具体的な `AbstractCentrallySymmetric` は、次の関数を定義する必要があります：

  * `center(::AbstractCentrallySymmetric)` – 中心点を返す

`AbstractCentrallySymmetric` のサブタイプ：

```jldoctest; setup = :(using LazySets: subtypes)
julia> subtypes(AbstractCentrallySymmetric)
2-element Vector{Any}:
 AbstractBallp
 Ellipsoid
```
