```
PeriodicBSplineBasis{k, T}
```

次数 `k` の Bスプラインおよびノット要素タイプ `T <: Real` のための Bスプライン基底。

基底はノットのセットと Bスプラインの次数によって定義されます。

---

```
PeriodicBSplineBasis(order::BSplineOrder{k}, ts::AbstractVector)
```

ノット `ts` を持つ次数 `k` の周期的 Bスプライン基底を作成します。

ノットの周期は `L = ts[end] - ts[begin]` として取られます。

# 例

周期 $L = 2$ の周期的領域上に Bスプライン基底を作成します。

```jldoctest
julia> ts = range(-1, 1; length = 11)
-1.0:0.2:1.0

julia> B = PeriodicBSplineBasis(BSplineOrder(4), ts)
10-element PeriodicBSplineBasis of order 4, domain [-1.0, 1.0), period 2.0
 knots: [..., -1.4, -1.2, -1.0, -0.8, -0.6, -0.4, -0.2, 0.0, 0.2, 0.4, 0.6, 0.8, 1.0, 1.2, ...]

julia> period(B)
2.0

julia> length(B)
10

julia> boundaries(B)
(-1.0, 1.0)

julia> B(-0.42)
(5, (0.12150000000000002, 0.6571666666666667, 0.22116666666666668, 0.00016666666666666563))

julia> B(-0.42 + 2)
(15, (0.12150000000000015, 0.6571666666666667, 0.22116666666666657, 0.00016666666666666674))

julia> knots(B)
14-element PeriodicKnots{Float64, 4, StepRangeLen{Float64, Base.TwicePrecision{Float64}, Base.TwicePrecision{Float64}, Int64}}:
 -1.4
 -1.2
 -1.0
 -0.8
 -0.6
 -0.4
 -0.2
  0.0
  0.2
  0.4
  0.6
  0.8
  1.0
  1.2
```
