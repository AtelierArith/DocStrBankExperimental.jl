```
set_name(model::GenericModel, name::AbstractString)
```

Set the [`MOI.Name`](@ref) attribute of `model`'s [`backend`](@ref) to `name`.

## Example

```jldoctest
julia> model = Model();

julia> set_name(model, "My Model")

julia> name(model)
"My Model"
```
