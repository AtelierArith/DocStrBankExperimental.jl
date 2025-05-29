```
show_objective_function_summary(io::IO, model::AbstractModel)
```

Write to `io` a summary of the objective function type.

## Extensions

`AbstractModel`s should implement this method.

## Example

```jldoctest
julia> model = Model();

julia> show_objective_function_summary(stdout, model)
Objective function type: AffExpr
```
