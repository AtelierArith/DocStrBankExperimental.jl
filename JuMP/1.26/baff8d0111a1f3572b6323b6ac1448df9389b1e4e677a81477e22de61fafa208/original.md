```
name(model::AbstractModel)
```

Return the [`MOI.Name`](@ref) attribute of `model`'s [`backend`](@ref), or a default if empty.

## Example

```jldoctest
julia> model = Model();

julia> name(model)
"A JuMP Model"
```
