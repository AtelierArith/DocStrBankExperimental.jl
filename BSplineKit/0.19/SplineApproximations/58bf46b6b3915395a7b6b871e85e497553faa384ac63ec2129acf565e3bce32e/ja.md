```
approximate(f, B::AbstractBSplineBasis, [method = ApproxByInterpolation(B)])
```

与えられた基底で関数 `f` を近似し、選択した方法を使用します。

精度（およびコスト）が低いものから高いものへ、可能な近似方法は次のとおりです：

  * [`VariationDiminishing`](@ref),
  * [`ApproxByInterpolation`](@ref),
  * [`MinimiseL2Error`](@ref)。

詳細については、それぞれのドキュメントを参照してください。

近似が行われた後は、インプレースの [`interpolate!`](@ref) を呼び出すことで、他の関数 `f` の追加の近似を効率的に行うことが可能です。これにより、メモリの割り当てを完全に回避し、計算時間を大幅に短縮します。

# 例

```jldoctest
julia> B = BSplineBasis(BSplineOrder(3), -1:0.4:1);

julia> S_interp = approximate(sin, B)
SplineApproximation containing the 7-element Spline{Float64}:
 basis: 7-element BSplineBasis of order 3, domain [-1.0, 1.0]
 order: 3
 knots: [-1.0, -1.0, -1.0, -0.6, -0.2, 0.2, 0.6, 1.0, 1.0, 1.0]
 coefficients: [-0.841471, -0.731727, -0.39727, 2.85767e-17, 0.39727, 0.731727, 0.841471]
 approximation method: interpolation at [-1.0, -0.8, -0.4, 0.0, 0.4, 0.8, 1.0]

julia> sin(0.3), S_interp(0.3)
(0.29552020666133955, 0.2959895327282942)

julia> approximate!(exp, S_interp)
SplineApproximation containing the 7-element Spline{Float64}:
 basis: 7-element BSplineBasis of order 3, domain [-1.0, 1.0]
 order: 3
 knots: [-1.0, -1.0, -1.0, -0.6, -0.2, 0.2, 0.6, 1.0, 1.0, 1.0]
 coefficients: [0.367879, 0.440373, 0.65701, 0.980127, 1.46223, 2.18111, 2.71828]
 approximation method: interpolation at [-1.0, -0.8, -0.4, 0.0, 0.4, 0.8, 1.0]

julia> exp(0.3), S_interp(0.3)
(1.3498588075760032, 1.3491015490105396)

julia> S_fast = approximate(exp, B, VariationDiminishing())
SplineApproximation containing the 7-element Spline{Float64}:
 basis: 7-element BSplineBasis of order 3, domain [-1.0, 1.0]
 order: 3
 knots: [-1.0, -1.0, -1.0, -0.6, -0.2, 0.2, 0.6, 1.0, 1.0, 1.0]
 coefficients: [0.367879, 0.449329, 0.67032, 1.0, 1.49182, 2.22554, 2.71828]
 approximation method: VariationDiminishing()

julia> S_opt = approximate(exp, B, MinimiseL2Error())
SplineApproximation containing the 7-element Spline{Float64}:
 basis: 7-element BSplineBasis of order 3, domain [-1.0, 1.0]
 order: 3
 knots: [-1.0, -1.0, -1.0, -0.6, -0.2, 0.2, 0.6, 1.0, 1.0, 1.0]
 coefficients: [0.368074, 0.440342, 0.657077, 0.980279, 1.46216, 2.18201, 2.71669]
 approximation method: MinimiseL2Error()

julia> x = 0.34; exp(x), S_opt(x), S_interp(x), S_fast(x)
(1.4049475905635938, 1.4044530324752076, 1.4044149581073813, 1.4328668494041878)
```
