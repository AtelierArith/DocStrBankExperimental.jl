```
knots(itp::AbstractInterpolation)
knots(etp::AbstractExtrapolation)
```

AbstractInterpolationまたはAbstractExtrapolationのためのノット位置のイテレータを返します。

イテレータは、単一次元の補間に対してスカラー値を生成し、高次元の補間に対しては座標のタプルを生成します。高次元のイテレーションは、各次元に沿ったノットの積として扱われます。

すなわち、Iterator.product(knots on 1st dim, knots on 2nd dim,...)

周期的または反射境界条件を持つ外挿は、無限のノットの列を生成します。

# 例

```jldoctest
julia> etp = linear_interpolation([1.0, 1.2, 2.3, 3.0], rand(4); extrapolation_bc=Periodic());

julia> Iterators.take(knots(etp), 5) |> collect
5-element Vector{Float64}:
 1.0
 1.2
 2.3
 3.0
 3.2
```
