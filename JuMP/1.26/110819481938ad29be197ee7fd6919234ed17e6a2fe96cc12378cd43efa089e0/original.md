```
callback_value(cb_data, x::GenericVariableRef)
callback_value(cb_data, x::Union{GenericAffExpr,GenericQuadExpr})
```

Return the primal solution of `x` inside a callback.

`cb_data` is the argument to the callback function, and the type is dependent on the solver.

Use [`callback_node_status`](@ref) to check whether a solution is available.

## Example

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
