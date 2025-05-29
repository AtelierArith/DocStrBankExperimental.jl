```
show_constraints_summary(io::IO, model::AbstractModel)
```

Write to `io` a summary of the number of constraints.

## Extensions

`AbstractModel`s should implement this method.

## Example

```jldoctest
julia> model = Model();

julia> @variable(model, x >= 0);

julia> show_constraints_summary(stdout, model)
`VariableRef`-in-`MathOptInterface.GreaterThan{Float64}`: 1 constraint
```
