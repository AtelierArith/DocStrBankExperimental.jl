```
mode(model::GenericModel)
```

Return the [`ModelMode`](@ref) of `model`.

## Example

```jldoctest
julia> model = Model();

julia> mode(model)
AUTOMATIC::ModelMode = 0
```
