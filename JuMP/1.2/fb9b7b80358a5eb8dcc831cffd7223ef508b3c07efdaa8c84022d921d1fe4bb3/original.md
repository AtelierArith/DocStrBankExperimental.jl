```
objective_function(model::Model,
               T::Type{<:AbstractJuMPScalar}=objective_function_type(model))
```

Return an object of type `T` representing the objective function. Error if the objective is not convertible to type `T`.

## Examples

```jldoctest objective_function; setup = :(using JuMP)
julia> model = Model()
A JuMP Model
Feasibility problem with:
Variables: 0
Model mode: AUTOMATIC
CachingOptimizer state: NO_OPTIMIZER
Solver name: No optimizer attached.

julia> @variable(model, x)
x

julia> @objective(model, Min, 2x + 1)
2 x + 1

julia> objective_function(model, AffExpr)
2 x + 1

julia> objective_function(model, QuadExpr)
2 x + 1

julia> typeof(objective_function(model, QuadExpr))
GenericQuadExpr{Float64,VariableRef}
```

We see with the last two commands that even if the objective function is affine, as it is convertible to a quadratic function, it can be queried as a quadratic function and the result is quadratic.

However, it is not convertible to a variable.

```jldoctest objective_function; filter = r"MathOptInterface\."s
julia> objective_function(model, VariableRef)
ERROR: InexactError: convert(MathOptInterface.VariableIndex, MathOptInterface.ScalarAffineFunction{Float64}(MathOptInterface.ScalarAffineTerm{Float64}[MathOptInterface.ScalarAffineTerm{Float64}(2.0, MathOptInterface.VariableIndex(1))], 1.0))
[...]
```
