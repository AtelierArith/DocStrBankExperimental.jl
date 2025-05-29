```
owner_model(v::AbstractVariableRef)
```

Returns the model to which `v` belongs.

## Example

```jldoctest
julia> model = Model();

julia> x = @variable(model)
_[1]

julia> owner_model(x) === model
true
```
