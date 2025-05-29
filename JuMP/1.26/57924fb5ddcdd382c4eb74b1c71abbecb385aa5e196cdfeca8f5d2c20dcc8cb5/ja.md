```
get_attribute(model::GenericModel, attr::MOI.AbstractModelAttribute)
get_attribute(x::GenericVariableRef, attr::MOI.AbstractVariableAttribute)
get_attribute(cr::ConstraintRef, attr::MOI.AbstractConstraintAttribute)
```

ソルバー特有の属性 `attr` の値を取得します。

これは、関連する MOI モデルで [`MOI.get`](@ref) を呼び出すことと同等であり、変数や制約の場合は、関連する [`MOI.VariableIndex`](@ref) または [`MOI.ConstraintIndex`](@ref) を使用します。

## 例

```jldoctest
julia> model = Model();

julia> @variable(model, x)
x

julia> @constraint(model, c, 2 * x <= 1)
c : 2 x ≤ 1

julia> get_attribute(model, MOI.Name())
""

julia> get_attribute(x, MOI.VariableName())
"x"

julia> get_attribute(c, MOI.ConstraintName())
"c"
```
