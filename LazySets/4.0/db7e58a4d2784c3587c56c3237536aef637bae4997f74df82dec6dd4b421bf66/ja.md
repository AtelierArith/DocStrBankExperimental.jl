# 拡張ヘルプ

```
isconvextype(::Type{<:LazySet})
```

### アルゴリズム

デフォルトの実装は `false` を返します。凸性を判断できるすべての集合型は、この動作をオーバーライドする必要があります。

### 例

無限ノルムのボールは常に凸です：

```jldoctest convex_types
julia> isconvextype(BallInf)
true
```

2つの集合の和集合（`UnionSet`）は、一般に凸であるかどうかは不明です。凸性は型情報だけでは決定できないため、`isconvextype` は `false` を返します。

```jldoctest convex_types
julia> isconvextype(UnionSet)
false
```

しかし、集合演算の型パラメータは、引数の型の凸性情報に基づいて、いくつかのケースで凸性を判断することを可能にします。遅延交差を考えてみましょう。2つの凸集合の交差は常に凸です：

```jldoctest convex_types
julia> isconvextype(Intersection{Float64, BallInf{Float64}, BallInf{Float64}})
true
```
