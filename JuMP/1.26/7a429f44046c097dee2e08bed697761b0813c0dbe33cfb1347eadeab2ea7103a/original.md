```
delete(model::GenericModel, variable_ref::GenericVariableRef)
```

Delete the variable associated with `variable_ref` from the model `model`.

Note that `delete` does not unregister the name from the model, so adding a new variable of the same name will throw an error. Use [`unregister`](@ref) to unregister the name after deletion.

## Example

```jldoctest
julia> model = Model();

julia> @variable(model, x)
x

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
