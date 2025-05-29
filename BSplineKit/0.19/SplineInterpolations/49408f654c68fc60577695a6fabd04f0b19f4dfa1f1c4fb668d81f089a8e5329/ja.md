```
interpolate(x, y, BSplineOrder(k), [bc = nothing])
```

Bスプラインの次数 `k` を使用して、位置 `x` での値 `y` を補間します。

グリッドポイント `x` は実数値でなければならず、増加順にあると仮定されます。

任意の中間点で評価できる [`SplineInterpolation`](@ref) を返します。

オプションで、[境界条件](@ref boundary-conditions-api) セクションにリストされている境界条件のいずれかを渡すことができます。現在、[`Natural`](@ref) および [`Periodic`](@ref) 境界条件が利用可能です。

また、[`interpolate!`](@ref) も参照してください。

!!! note "周期的境界条件"
    補間されたデータが周期信号を表すことになっている場合は、周期的境界条件を使用する必要があります。この場合、`bc = Period(L)` を渡します。ここで `L` は x 軸の周期です。端点 `x[begin] + L` は `x` ベクターに含めてはいけません。


!!! note "三次周期スプライン"
    *三次*周期スプライン (`BSplineOrder(4)`) は、他の次数の周期スプラインと比較して特に最適化されています。三次周期スプラインを使用した補間は、入力（`x` および `y` の値を含む）を変更することに注意してください。


# 例

```jldoctest interpolate
julia> xs = -1:0.1:1;

julia> ys = cospi.(xs);

julia> S = interpolate(xs, ys, BSplineOrder(4))
SplineInterpolation containing the 21-element Spline{Float64}:
 basis: 21-element BSplineBasis of order 4, domain [-1.0, 1.0]
 order: 4
 knots: [-1.0, -1.0, -1.0, -1.0, -0.8, -0.7, -0.6, -0.5, -0.4, -0.3  …  0.3, 0.4, 0.5, 0.6, 0.7, 0.8, 1.0, 1.0, 1.0, 1.0]
 coefficients: [-1.0, -1.00111, -0.8975, -0.597515, -0.314147, 1.3265e-6, 0.314142, 0.597534, 0.822435, 0.96683  …  0.96683, 0.822435, 0.597534, 0.314142, 1.3265e-6, -0.314147, -0.597515, -0.8975, -1.00111, -1.0]
 interpolation points: -1.0:0.1:1.0

julia> S(-1)
-1.0

julia> (Derivative(1) * S)(-1)
-0.01663433622896893

julia> (Derivative(2) * S)(-1)
10.527273287554928

julia> Snat = interpolate(xs, ys, BSplineOrder(4), Natural())
SplineInterpolation containing the 21-element Spline{Float64}:
 basis: 21-element RecombinedBSplineBasis of order 4, domain [-1.0, 1.0], BCs {left => (D{2},), right => (D{2},)}
 order: 4
 knots: [-1.0, -1.0, -1.0, -1.0, -0.9, -0.8, -0.7, -0.6, -0.5, -0.4  …  0.4, 0.5, 0.6, 0.7, 0.8, 0.9, 1.0, 1.0, 1.0, 1.0]
 coefficients: [-0.833333, -0.647516, -0.821244, -0.597853, -0.314057, -2.29076e-5, 0.314148, 0.597532, 0.822435, 0.96683  …  0.96683, 0.822435, 0.597532, 0.314148, -2.29076e-5, -0.314057, -0.597853, -0.821244, -0.647516, -0.833333]
 interpolation points: -1.0:0.1:1.0

julia> Snat(-1)
-1.0

julia> (Derivative(1) * Snat)(-1)
0.2872618670889516

julia> (Derivative(2) * Snat)(-1)
-3.33066907387547e-14

```

## 周期的境界条件

$$
f(x) = \cos(πx)
$$

を $x ∈ [-1, 1)$ で補間します。周期は $L = 2$ であり、端点 ($x = 1$) はデータポイントに含めてはいけません。

```jldoctest interpolate
julia> xp = -1:0.1:0.9;

julia> yp = cospi.(xp);

julia> Sper = interpolate(xp, yp, BSplineOrder(4), Periodic(2))
SplineInterpolation containing the 20-element Spline{Float64}:
 basis: 20-element PeriodicBSplineBasis of order 4, domain [-1.0, 1.0), period 2.0
 order: 4
 knots: [..., -1.2, -1.1, -1.0, -0.9, -0.8, -0.7, -0.6, -0.5, -0.4, -0.3  …  0.2, 0.3, 0.4, 0.5, 0.6, 0.7, 0.8, 0.9, 1.0, 1.1, ...]
 coefficients: [..., -1.01659, -0.96683, -0.822435, -0.597534, -0.314142, 1.10589e-17, 0.314142, 0.597534, 0.822435, 0.96683, 1.01659, 0.96683, 0.822435, 0.597534, 0.314142, 1.51788e-17, -0.314142, -0.597534, -0.822435, -0.96683, ...]
 interpolation points: -1.0:0.1:0.9
```

予想通り、周期スプラインは境界近くの周期関数 $f(x) = \cos(πx)$ をより良く近似します：

```jldoctest interpolate
julia> x = -0.99; cospi(x), Sper(x), Snat(x), S(x)
(-0.9995065603657316, -0.9995032595823043, -0.9971071640321145, -0.9996420091470221)

julia> x = 0.998; cospi(x), Sper(x), Snat(x), S(x)
(-0.9999802608561371, -0.9999801044078943, -0.9994253145274461, -1.0000122303614758)
```
