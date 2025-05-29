```
LazySet{N}
```

LazySetsにおける集合型の抽象型。

### 注意事項

`LazySet`型は、異なる数値型を使用するために、通常は`N<:Real`の型`N`でパラメータ化されるべきです。

すべての`LazySet`は、以下の関数を実装しなければなりません：

  * `dim(X::LazySet)` – `X`の周囲の次元

厳密には必要ではありませんが、以下の関数を実装することは有用です：

  * `σ(d::AbstractVector, X::LazySet)` – 与えられた方向`d`における`X`のサポートベクトル

関数

  * `ρ(d::AbstractVector, X::LazySet)` – 与えられた方向`d`における`X`のサポート関数

の実装はオプションですが、`σ`に依存するフォールバック実装があるため、必須ではありません。しかし、潜在的に無限大の集合（ほとんどの遅延集合型を含む）に対しては、このフォールバックは使用できず、明示的な実装を提供する必要があります。

`LazySet`のサブタイプ（抽象インターフェースを含む）：

```jldoctest; setup = :(using LazySets: subtypes)
julia> subtypes(LazySet, false)
17-element Vector{Any}:
 AbstractAffineMap
 AbstractPolynomialZonotope
 Bloating
 CachedMinkowskiSumArray
 CartesianProduct
 CartesianProductArray
 Complement
 ConvexSet
 Intersection
 IntersectionArray
 MinkowskiSum
 MinkowskiSumArray
 Polygon
 QuadraticMap
 Rectification
 UnionSet
 UnionSetArray
```

*具体的な*サブタイプのみを考慮すると、次のようになります：

```jldoctest; setup = :(using LazySets: subtypes)
julia> concrete_subtypes = subtypes(LazySet, true);

julia> length(concrete_subtypes)
53

julia> println.(concrete_subtypes);
AffineMap
Ball1
Ball2
BallInf
Ballp
Bloating
CachedMinkowskiSumArray
CartesianProduct
CartesianProductArray
Complement
ConvexHull
ConvexHullArray
DensePolynomialZonotope
Ellipsoid
EmptySet
ExponentialMap
ExponentialProjectionMap
HParallelotope
HPolygon
HPolygonOpt
HPolyhedron
HPolytope
HalfSpace
Hyperplane
Hyperrectangle
Intersection
IntersectionArray
Interval
InverseLinearMap
Line
Line2D
LineSegment
LinearMap
MinkowskiSum
MinkowskiSumArray
Polygon
QuadraticMap
Rectification
ResetMap
SimpleSparsePolynomialZonotope
Singleton
SparsePolynomialZonotope
Star
SymmetricIntervalHull
Tetrahedron
Translation
UnionSet
UnionSetArray
Universe
VPolygon
VPolytope
ZeroSet
Zonotope

```
