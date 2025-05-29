```
delete(model::GenericModel, variable_refs::Vector{<:GenericVariableRef})
```

Delete the variables associated with `variable_refs` from the model `model`. Solvers may implement methods for deleting multiple variables that are more efficient than repeatedly calling the single variable delete method.

See also: [`unregister`](@ref)

## Example

```jldoctest
julia> model = Model();

julia> @variable(model, x[1:2]);

julia> delete(model, x)

julia> unregister(model, :x)

julia> print(model)
Feasibility
Subject to

julia> model[:x]
ERROR: KeyError: key :x not found
Stacktrace:
[...]
```
