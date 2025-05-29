```
objective_function_string(mode, model::AbstractModel)::String
```

Return a `String` describing the objective function of the model.

## Example

```jldoctest
julia> model = Model();

julia> @variable(model, x);

julia> @objective(model, Min, 2 * x);

julia> objective_function_string(MIME("text/plain"), model)
"2 x"
```
