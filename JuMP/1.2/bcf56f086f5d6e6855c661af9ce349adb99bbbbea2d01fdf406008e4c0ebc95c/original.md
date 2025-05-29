```
num_constraints(model::Model; count_variable_in_set_constraints::Bool)
```

Return the number of constraints in `model`.

If `count_variable_in_set_constraints == true`, then `VariableRef` constraints such as `VariableRef`-in-`Integer` are included. To count only the number of structural constraints (e.g., the rows in the constraint matrix of a linear program), pass `count_variable_in_set_constraints = false`.

## Examples

```jldoctest; setup=:(using JuMP)
julia> model = Model();

julia> @variable(model, x >= 0, Int);

julia> @constraint(model, 2x <= 1);

julia> num_constraints(model; count_variable_in_set_constraints = true)
3

julia> num_constraints(model; count_variable_in_set_constraints = false)
1
```
