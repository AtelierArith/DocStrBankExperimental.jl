```
isempty(model::GenericModel)
```

Verifies whether the model is empty, that is, whether the MOI backend is empty and whether the model is in the same state as at its creation, apart from optimizer attributes.

## Example

```jldoctest
julia> model = Model();

julia> isempty(model)
true

julia> @variable(model, x[1:2]);

julia> isempty(model)
false
```
