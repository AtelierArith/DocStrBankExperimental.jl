```
callback_value(cb_data, x::GenericVariableRef)
callback_value(cb_data, x::Union{GenericAffExpr,GenericQuadExpr})
```

コールバック内での `x` の原始解を返します。

`cb_data` はコールバック関数への引数であり、その型はソルバーに依存します。

解が利用可能かどうかを確認するには [`callback_node_status`](@ref) を使用してください。

## 例

```julia
julia> import Gurobi

julia> model = Model(Gurobi.Optimizer);

julia> set_silent(model)

julia> @variable(model, x <= 10, Int);

julia> @objective(model, Max, x);

julia> function my_callback_function(cb_data, cb_where)
           status = callback_node_status(cb_data, model)
           if status == MOI.CALLBACK_NODE_STATUS_INTEGER
               Gurobi.load_callback_variable_primal(cb_data, cb_where)
               println("Solution is: ", callback_value(cb_data, x))
           end
           return
       end
my_callback_function (generic function with 1 method)

julia> set_attribute(model, Gurobi.CallbackFunction(), my_callback_function)

julia> optimize!(model)
Solution is: 10.0
```
