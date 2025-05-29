```
num_variables(model::GenericModel)::Int64
```

Returns number of variables in `model`.

## Example

```jldoctest
julia> model = Model();

julia> @variable(model, x[1:2]);

julia> num_variables(model)
2
```
