```
owner_model(s::AbstractJuMPScalar)
```

Return the model owning the scalar `s`.

## Example

```jldoctest
julia> model = Model();

julia> @variable(model, x);

julia> owner_model(x) === model
true
```
