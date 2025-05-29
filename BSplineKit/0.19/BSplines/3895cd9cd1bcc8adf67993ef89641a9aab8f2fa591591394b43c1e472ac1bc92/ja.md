```
getindex(B::AbstractBSplineBasis, i, [T = Float64])
```

$$
i
$$

-番目の基底関数を取得します。

これは `BasisFunction(B, i, T)` のエイリアスです（詳細は [`BasisFunction`](@ref) を参照してください）。

返されるオブジェクトは、基底によって定義された境界内の任意の点で評価できます。

# 例

```jldoctest
julia> B = BSplineBasis(BSplineOrder(4), -1:0.1:1)
23-element BSplineBasis of order 4, domain [-1.0, 1.0]
 knots: [-1.0, -1.0, -1.0, -1.0, -0.9, -0.8, -0.7, -0.6, -0.5, -0.4  …  0.4, 0.5, 0.6, 0.7, 0.8, 0.9, 1.0, 1.0, 1.0, 1.0]

julia> B[6]
Basis function i = 6
  from 23-element BSplineBasis of order 4, domain [-1.0, 1.0]
  support: [-0.8, -0.4) (knots 6:10)

julia> B[6](-0.5)
0.16666666666666666

julia> B[6, Float32](-0.5)
0.16666667f0

julia> B[6](-0.5, Derivative(1))
-5.000000000000001
```
