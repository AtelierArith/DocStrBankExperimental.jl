```
JuMP.set_objective_coefficient(model::InfiniteModel,
                               variable::GeneralVariableRef,
                               coefficient::Real)::Nothing
```

`JuMP.set_objective_coefficient`を拡張します。`variable`に関連付けられた線形目的係数を`coefficient`に設定します。関数の型がサポートされていない場合はエラーが発生します。

**例**

```julia-repl
julia> @variable(model, x)
x

julia> @variable(model, y)
y

julia> @objective(model, x + y)
x + y

julia> set_objective_coefficient(model, y, 2)

julia> objective_function(model)
x + 2 y
```
