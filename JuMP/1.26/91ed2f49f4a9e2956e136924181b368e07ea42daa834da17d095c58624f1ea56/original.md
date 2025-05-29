```
is_valid(model::GenericModel, variable_ref::GenericVariableRef)
```

Return `true` if `variable` refers to a valid variable in `model`.

## Example

```jldoctest
julia> model = Model();

julia> @variable(model, x);

julia> is_valid(model, x)
true

julia> model_2 = Model();

julia> is_valid(model_2, x)
false
```
