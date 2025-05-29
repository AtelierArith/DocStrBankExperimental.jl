```
lp_sensitivity_report(model::Model; atol::Float64 = 1e-8)::SensitivityReport
```

現在の最適基準を持つ線形プログラム `model` に対して、[`SensitivityReport`](@ref) オブジェクトを返します。このオブジェクトは次のようにマッピングされます：

  * 各変数参照に対して、タプル `(d_lo, d_hi)::Tuple{Float64,Float64}` を返し、対応する変数の目的係数がどれだけ変化できるかを説明します。これにより、元の基準が最適であり続けます。
  * 各制約参照に対して、タプル `(d_lo, d_hi)::Tuple{Float64,Float64}` を返し、対応する制約の右辺がどれだけ変化できるかを説明します。これにより、基準が最適であり続けます。

両方のタプルは相対的であり、絶対的ではありません。したがって、目的係数が `1.0` でタプル `(-0.5, 0.5)` がある場合、目的係数は `1.0 - 0.5` と `1.0 + 0.5` の間で変動できます。

`atol` はプライマル/デュアル最適性の許容誤差であり、基準を計算するために使用されるソルバーの許容誤差と一致する必要があります。

注意：区間制約はサポートされていません。

# 例

```
model = Model(HiGHS.Optimizer)
@variable(model, -1 <= x <= 2)
@objective(model, Min, x)
optimize!(model)
report = lp_sensitivity_report(model; atol = 1e-7)
dx_lo, dx_hi = report[x]
println(
    "The objective coefficient of `x` can decrease by $dx_lo or " *
    "increase by $dx_hi."
)
c = LowerBoundRef(x)
dRHS_lo, dRHS_hi = report[c]
println(
    "The lower bound of `x` can decrease by $dRHS_lo or increase " *
    "by $dRHS_hi."
)
```
