```
approximate(f, basis::BSplineBasis; indices=eachindex(basis)) -> Spline
```

関数 `f` を Bスプライン基底 `basis` で近似します。`indices` が指定されている場合、`basis` の指定されたインデックスの基底関数のみが使用されます。

近似は、基底の [`knotaverages`](@ref) での `f` のサンプルを補間することによって計算されます。

参照: [`interpolate`](@ref)

# 例

```jldoctest
julia> basis = BSplineBasis(6, 0:0.25:1);

julia> spl = approximate(sin, basis, indices=2:length(basis))
BSplines.Spline{BSplines.BSplineBasis{StepRangeLen{Float64, Base.TwicePrecision{Float64}, Base.TwicePrecision{Float64}, Int64}}, Vector{Float64}}:
 basis: 9-element BSplines.BSplineBasis{StepRangeLen{Float64, Base.TwicePrecision{Float64}, Base.TwicePrecision{Float64}, Int64}}:
  order: 6
  breakpoints: 0.0:0.25:1.0
 coeffs: [0.0, 0.05, 0.15, 0.298438, 0.486979, 0.651299, 0.755166, 0.814456, 0.841471]

julia> spl(π/4) ≈ sqrt(1/2)
true
```
