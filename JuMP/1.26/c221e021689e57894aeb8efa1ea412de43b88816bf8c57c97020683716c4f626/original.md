```
objective_function(
    model::GenericModel,
    ::Type{F} = objective_function_type(model),
) where {F}
```

Return an object of type `F` representing the objective function.

Errors if the objective is not convertible to type `F`.

This function is equivalent to querying the [`MOI.ObjectiveFunction{F}`](@ref) attribute.

## Example

```jldoctest objective_function
julia> model = Model();

julia> @variable(model, x)
x

julia> @objective(model, Min, 2x + 1)
2 x + 1

julia> objective_function(model, AffExpr)
2 x + 1

julia> objective_function(model, QuadExpr)
2 x + 1

julia> typeof(objective_function(model, QuadExpr))
QuadExpr (alias for GenericQuadExpr{Float64, GenericVariableRef{Float64}})
```

We see with the last two commands that even if the objective function is affine, as it is convertible to a quadratic function, it can be queried as a quadratic function and the result is quadratic.

However, it is not convertible to a variable:

```jldoctest objective_function; filter = r"MathOptInterface\."s
julia> objective_function(model, VariableRef)
ERROR: InexactError: convert(MathOptInterface.VariableIndex, 1.0 + 2.0 MOI.VariableIndex(1))
[...]
```
