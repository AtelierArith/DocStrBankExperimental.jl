```
is_valid(model::GenericModel, con_ref::ConstraintRef{<:AbstractModel})
```

Return `true` if `con_ref` refers to a valid constraint in `model`.

## Example

```jldoctest
julia> model = Model();

julia> @variable(model, x);

julia> @constraint(model, c, 2 * x <= 1);

julia> is_valid(model, c)
true

julia> model_2 = Model();

julia> is_valid(model_2, c)
false
```
