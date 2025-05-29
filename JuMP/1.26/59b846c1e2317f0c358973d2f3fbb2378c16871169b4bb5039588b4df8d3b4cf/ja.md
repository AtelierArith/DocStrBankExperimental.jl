```
callback_node_status(cb_data, model::GenericModel)
```

[`MOI.CallbackNodeStatusCode`](@ref) 列挙型を返し、[`callback_value`](@ref) から得られる現在のプライマル解が整数的に実現可能かどうかを示します。

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
               println("Status is: ", status)
           end
           return
       end
my_callback_function (generic function with 1 method)

julia> set_attribute(model, Gurobi.CallbackFunction(), my_callback_function)

julia> optimize!(model)
Status is: CALLBACK_NODE_STATUS_INTEGER
```
