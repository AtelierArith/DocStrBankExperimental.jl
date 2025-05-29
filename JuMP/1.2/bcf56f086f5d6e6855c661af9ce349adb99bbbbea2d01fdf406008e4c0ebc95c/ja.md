```
num_constraints(model::Model; count_variable_in_set_constraints::Bool)
```

`model`内の制約の数を返します。

`count_variable_in_set_constraints == true`の場合、`VariableRef`制約（例えば、`VariableRef`-in-`Integer`）が含まれます。構造的制約の数のみをカウントするには（例えば、線形プログラムの制約行列の行）、`count_variable_in_set_constraints = false`を渡してください。

## 例

```jldoctest; setup=:(using JuMP)
julia> model = Model();

julia> @variable(model, x >= 0, Int);

julia> @constraint(model, 2x <= 1);

julia> num_constraints(model; count_variable_in_set_constraints = true)
3

julia> num_constraints(model; count_variable_in_set_constraints = false)
1
```
