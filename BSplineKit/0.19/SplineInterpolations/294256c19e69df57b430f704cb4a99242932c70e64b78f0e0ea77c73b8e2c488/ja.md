```
fit(BSplineOrder(4), xs, ys, λ::Real, [bc = Natural()]; [weights = nothing])
```

与えられたデータに対して三次スムージングスプラインをフィットさせます。

スムージングパラメータ $λ$ を考慮して、データ（点 `(xs[i], ys[i])`）を大まかに通過する三次スプラインを返します。$λ = 0$ はスムージングなしを意味し、結果はすべてのデータと同等です。

異なるデータポイントに異なる重みを与えたい場合（例えば、曲線が特定の点にできるだけ近づくようにしたい場合）、オプションで `weights` ベクトルを渡すことができます。デフォルトではすべての重みは $w_i = 1$ です。

より正確には、返されるスプライン $S(x)$ は次の式を最小化します：

$$
∑_{i = 1}^N w_i |y_i - S(x_i)|^2 + λ ∫_{x_1}^{x_N} \left[ S''(x) \right]^2 \, \mathrm{d}x
$$

現在、三次スプライン（`BSplineOrder(4)`）のみがサポートされています。他の `StatsAPI.fit` の実装との衝突を避けるために、最初の引数として明示的に `BSplineOrder(4)` を渡す必要があります。

境界条件（`bc`）は、周期的スプラインの場合は [`Periodic`](@ref) である必要があり、それ以外の場合は [`Natural`](@ref) である必要があります（これがデフォルトです）。 （現在、周期的なケースはデフォルトの自然条件よりもはるかに遅くなる可能性があります。）

# 例

```jldoctest smoothing_spline
julia> xs = (0:0.01:1).^2;

julia> ys = @. cospi(2 * xs) + 0.1 * sinpi(200 * xs);  # スムーズ + 高度に変動する成分

julia> λ = 0.001;  # スムージングパラメータ

julia> S = fit(BSplineOrder(4), xs, ys, λ)
101-element Spline{Float64}:
 basis: 101-element RecombinedBSplineBasis of order 4, domain [0.0, 1.0], BCs {left => (D{2},), right => (D{2},)}
 order: 4
 knots: [0.0, 0.0, 0.0, 0.0, 0.0001, 0.0004, 0.0009, 0.0016, 0.0025, 0.0036  …  0.8836, 0.9025, 0.9216, 0.9409, 0.9604, 0.9801, 1.0, 1.0, 1.0, 1.0]
 coefficients: [0.946872, 0.631018, 1.05101, 1.04986, 1.04825, 1.04618, 1.04366, 1.04067, 1.03722, 1.03331  …  0.437844, 0.534546, 0.627651, 0.716043, 0.798813, 0.875733, 0.947428, 1.01524, 0.721199, 0.954231]
```
