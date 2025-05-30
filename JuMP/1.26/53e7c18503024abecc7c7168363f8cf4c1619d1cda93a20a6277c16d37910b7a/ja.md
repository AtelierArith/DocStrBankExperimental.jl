```
lp_sensitivity_report(model::GenericModel{T}; atol::T = Base.rtoldefault(T))::SensitivityReport{T} where {T}
```

現在の最適基準を持つ線形プログラム `model` に対して、元の基準が最適であり続けるために、対応する変数の目的係数がどれだけ変化できるかを説明するタプル `(d_lo, d_hi)::Tuple{T,T}` にマッピングされる [`SensitivityReport`](@ref) オブジェクトを返します。

  * すべての変数参照に対して、目的係数がどれだけ変化できるかを説明するタプル `(d_lo, d_hi)::Tuple{T,T}`。
  * すべての制約参照に対して、対応する制約の右辺がどれだけ変化できるかを説明するタプル `(d_lo, d_hi)::Tuple{T,T}`。

両方のタプルは相対的であり、絶対的ではありません。したがって、目的係数が `1.0` でタプル `(-0.5, 0.5)` がある場合、目的係数は `1.0 - 0.5` と `1.0 + 0.5` の間で変動できます。

`atol` はプライマル/デュアル最適性の許容誤差であり、基準を計算するために使用されるソルバーの許容誤差と一致する必要があります。

注意: 区間制約はサポートされていません。

## 例

```jldoctest
julia> import HiGHS

julia> model = Model(HiGHS.Optimizer);

julia> set_silent(model)

julia> @variable(model, -1 <= x <= 2)
x

julia> @objective(model, Min, x)
x

julia> optimize!(model)

julia> report = lp_sensitivity_report(model; atol = 1e-7);

julia> dx_lo, dx_hi = report[x]
(-1.0, Inf)

julia> println(
           "The objective coefficient of `x` can decrease by $dx_lo or " *
           "increase by $dx_hi."
       )
The objective coefficient of `x` can decrease by -1.0 or increase by Inf.

julia> dRHS_lo, dRHS_hi = report[LowerBoundRef(x)]
(-Inf, 3.0)

julia> println(
           "The lower bound of `x` can decrease by $dRHS_lo or increase " *
           "by $dRHS_hi."
       )
The lower bound of `x` can decrease by -Inf or increase by 3.0.
```
