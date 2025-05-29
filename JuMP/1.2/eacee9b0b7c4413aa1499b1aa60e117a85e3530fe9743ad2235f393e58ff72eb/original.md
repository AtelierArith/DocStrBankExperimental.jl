```
all_constraints(
    model::Model;
    include_variable_in_set_constraints::Bool,
)::Vector{ConstraintRef}
```

Return a list of all constraints in `model`.

If `include_variable_in_set_constraints == true`, then `VariableRef` constraints such as `VariableRef`-in-`Integer` are included. To return only the structural constraints (e.g., the rows in the constraint matrix of a linear program), pass `include_variable_in_set_constraints = false`.

## Examples

```jldoctest; setup=:(using JuMP)
julia> model = Model();

julia> @variable(model, x >= 0, Int);

julia> @constraint(model, 2x <= 1);

julia> @NLconstraint(model, x^2 <= 1);

julia> all_constraints(model; include_variable_in_set_constraints = true)
4-element Vector{ConstraintRef}:
 2 x ≤ 1.0
 x ≥ 0.0
 x integer
 x ^ 2.0 - 1.0 ≤ 0

julia> all_constraints(model; include_variable_in_set_constraints = false)
2-element Vector{ConstraintRef}:
 2 x ≤ 1.0
 x ^ 2.0 - 1.0 ≤ 0
```

## Performance considerations

Note that this function is type-unstable because it returns an abstractly typed vector. If performance is a problem, consider using [`list_of_constraint_types`](@ref) and a function barrier. See the [Performance tips for extensions](@ref) section of the documentation for more details.
