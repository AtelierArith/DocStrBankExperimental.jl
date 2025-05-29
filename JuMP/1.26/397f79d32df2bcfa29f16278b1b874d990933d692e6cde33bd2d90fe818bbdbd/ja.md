```
set_attribute(model::GenericModel, attr::MOI.AbstractModelAttribute, value)
set_attribute(x::GenericVariableRef, attr::MOI.AbstractVariableAttribute, value)
set_attribute(cr::ConstraintRef, attr::MOI.AbstractConstraintAttribute, value)
```

ソルバー特有の属性 `attr` の値を `value` に設定します。

これは、関連する MOI モデルで [`MOI.set`](@ref) を呼び出すことと同等であり、変数や制約の場合は、関連する [`MOI.VariableIndex`](@ref) または [`MOI.ConstraintIndex`](@ref) を使用します。

## 例

```jldoctest
julia> model = Model();

julia> @variable(model, x)
x

julia> @constraint(model, c, 2 * x <= 1)
c : 2 x ≤ 1

julia> set_attribute(model, MOI.Name(), "model_new")

julia> set_attribute(x, MOI.VariableName(), "x_new")

julia> set_attribute(c, MOI.ConstraintName(), "c_new")
```
