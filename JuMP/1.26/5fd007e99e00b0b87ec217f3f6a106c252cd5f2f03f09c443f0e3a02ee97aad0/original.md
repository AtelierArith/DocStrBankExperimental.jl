```
check_belongs_to_model(x::AbstractJuMPScalar, model::AbstractModel)
check_belongs_to_model(x::AbstractConstraint, model::AbstractModel)
```

Throw [`VariableNotOwned`](@ref) if the [`owner_model`](@ref) of `x` is not `model`.

## Example

```jldoctest
julia> model = Model();

julia> @variable(model, x);

julia> check_belongs_to_model(x, model)

julia> model_2 = Model();

julia> check_belongs_to_model(x, model_2)
ERROR: VariableNotOwned{VariableRef}(x): the variable x cannot be used in this model because
it belongs to a different model.
[...]
```
