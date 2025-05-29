```
list_of_constraint_types(model::Model)::Vector{Tuple{Type,Type}}
```

Return a list of tuples of the form `(F, S)` where `F` is a JuMP function type and `S` is an MOI set type such that `all_constraints(model, F, S)` returns a nonempty list.

# Example

```jldoctest; setup=:(using JuMP)
julia> model = Model();

julia> @variable(model, x >= 0, Bin);

julia> @constraint(model, 2x <= 1);

julia> list_of_constraint_types(model)
3-element Array{Tuple{Type,Type},1}:
 (GenericAffExpr{Float64,VariableRef}, MathOptInterface.LessThan{Float64})
 (VariableRef, MathOptInterface.GreaterThan{Float64})
 (VariableRef, MathOptInterface.ZeroOne)
```

## Performance considerations

Iterating over the list of function and set types is a type-unstable operation. Consider using a function barrier. See the [Performance tips for extensions](@ref) section of the documentation for more details.
