```
compute_conflict!(model::GenericModel)
```

モデルが非可行である場合にコンフリクトを計算します。

コンフリクトは、不可約非可行サブシステム（IIS）とも呼ばれます。

まだオプティマイザが設定されていない場合（[`set_optimizer`](@ref)を参照）、[`NoOptimizer`](@ref)エラーがスローされます。

コンフリクトのステータスは、[`MOI.ConflictStatus`](@ref)モデル属性で確認できます。次に、各制約のステータスは、[`MOI.ConstraintConflictStatus`](@ref)属性で照会できます。

関連情報: [`copy_conflict`](@ref)

## 例

```julia
julia> using JuMP

julia> model = Model(Gurobi.Optimizer);

julia> set_silent(model)

julia> @variable(model, x >= 0);

julia> @constraint(model, c1, x >= 2);

julia> @constraint(model, c2, x <= 1);

julia> optimize!(model)

julia> compute_conflict!(model)

julia> get_attribute(model, MOI.ConflictStatus())
CONFLICT_FOUND::ConflictStatusCode = 3
```
