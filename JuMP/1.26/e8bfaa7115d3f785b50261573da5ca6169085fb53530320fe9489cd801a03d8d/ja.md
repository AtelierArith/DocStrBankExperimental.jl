```
shadow_price(con_ref::ConstraintRef)
```

制約の無限小緩和から目的関数の変化を返します。

シャドウプライスは[`dual`](@ref)から計算され、[`objective_sense`](@ref)が[`MIN_SENSE`](@ref)または[`MAX_SENSE`](@ref)（[`FEASIBILITY_SENSE`](@ref)ではない）であるときのみ照会できます。

また、[`reduced_cost`](@ref)も参照してください。

## `dual`との比較

シャドウプライスは、[`objective_sense`](@ref)に応じて[`dual`](@ref)値と符号が異なる場合があります。違いは以下の表にまとめられています。

|             |      `MIN_SENSE` |      `MAX_SENSE` |
| -----------:| ----------------:| ----------------:|
| `f(x) <= b` |  `dual(con_ref)` | `-dual(con_ref)` |
| `f(x) >= b` | `-dual(con_ref)` |  `dual(con_ref)` |

## 注意事項

この関数は単に[`dual`](@ref)から符号を変換するだけで、シャドウプライスの感度解釈を保証するために必要な条件を検証しません。呼び出し元は、例えば、ソルバーが最適なプライマル-デュアルペアに収束したか、または不適合の証明を確認する責任があります。

等式制約の緩和（したがってシャドウプライス）は、どの等式制約の感覚がアクティブであるかに基づいて定義されます。

## 例

```jldoctest
julia> import HiGHS

julia> model = Model(HiGHS.Optimizer);

julia> set_silent(model)

julia> @variable(model, x);

julia> @constraint(model, c, x <= 1)
c : x ≤ 1

julia> @objective(model, Max, 2 * x + 1);

julia> optimize!(model)

julia> dual_status(model)
FEASIBLE_POINT::ResultStatusCode = 1

julia> shadow_price(c)
2.0

julia> dual(c)
-2.0
```
