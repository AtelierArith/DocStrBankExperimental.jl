```
LessThan{T<:Real}(upper::T)
```

The set $(-\infty, upper] \subseteq \mathbb{R}$.

## Example

```jldoctest
julia> model = MOI.Utilities.Model{Float64}();

julia> x = MOI.add_variable(model)
MOI.VariableIndex(1)

julia> MOI.add_constraint(model, x, MOI.LessThan(2.0))
MathOptInterface.ConstraintIndex{MathOptInterface.VariableIndex, MathOptInterface.LessThan{Float64}}(1)
```
