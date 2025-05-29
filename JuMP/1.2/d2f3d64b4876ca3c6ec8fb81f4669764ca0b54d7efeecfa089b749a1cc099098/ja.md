```
primal_feasibility_report(
    model::Model,
    point::AbstractDict{VariableRef,Float64} = _last_primal_solution(model),
    atol::Float64 = 0.0,
    skip_missing::Bool = false,
)::Dict{Any,Float64}
```

辞書 `point` が変数を原始値にマッピングしている場合、供給された許容誤差 `atol` よりも不適合性が大きい制約をキーとする辞書を返します。各キーに対応する値は、それぞれの不適合性です。不適合性は、制約の原始値（`MOI.ConstraintPrimal` を参照）と、対応する集合内の最近接点とのユークリッド距離として定義されます。

## 注意事項

  * `skip_missing = true` の場合、`point` に含まれていない変数を含む制約は無視されます。
  * `skip_missing = false` で部分的な原始解が提供された場合、エラーが発生します。
  * ポイントが提供されていない場合、モデルが最後に解かれたときの原始解が使用されます。

## 例

```jldoctest; setup=:(using JuMP)
julia> model = Model();

julia> @variable(model, 0.5 <= x <= 1);

julia> primal_feasibility_report(model, Dict(x => 0.2))
Dict{Any,Float64} with 1 entry:
  x ≥ 0.5 => 0.3
```
