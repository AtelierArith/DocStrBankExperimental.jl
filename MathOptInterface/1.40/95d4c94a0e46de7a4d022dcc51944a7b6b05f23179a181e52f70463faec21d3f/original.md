```
EqualTo{T<:Number}(value::T)
```

The set containing the single point $\{value\} \subseteq \mathbb{R}$.

## Example

```jldoctest
julia> model = MOI.Utilities.Model{Float64}();

julia> x = MOI.add_variable(model)
MOI.VariableIndex(1)

julia> MOI.add_constraint(model, x, MOI.EqualTo(2.0))
MathOptInterface.ConstraintIndex{MathOptInterface.VariableIndex, MathOptInterface.EqualTo{Float64}}(1)
```
