```
all_variables(model::GenericModel{T})::Vector{GenericVariableRef{T}} where {T}
```

Returns a list of all variables currently in the model. The variables are ordered by creation time.

## Example

```jldoctest
julia> model = Model();

julia> @variable(model, x);

julia> @variable(model, y);

julia> all_variables(model)
2-element Vector{VariableRef}:
 x
 y
```
