```
check_belongs_to_model(x::AbstractJuMPScalar, model::AbstractModel)
check_belongs_to_model(x::AbstractConstraint, model::AbstractModel)
```

[`owner_model`](@ref) が `x` のものでない場合、[`VariableNotOwned`](@ref) をスローします。

## 例

```jldoctest
julia> model = Model();

julia> @variable(model, x);

julia> check_belongs_to_model(x, model)

julia> model_2 = Model();

julia> check_belongs_to_model(x, model_2)
ERROR: VariableNotOwned{VariableRef}(x): 変数 x は異なるモデルに属しているため、このモデルで使用できません。
[...]
```
