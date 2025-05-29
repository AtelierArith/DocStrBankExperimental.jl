```
LessThan{T<:Real}(upper::T)
```

集合 $(-\infty, upper] \subseteq \mathbb{R}$。

## 例

```jldoctest
julia> model = MOI.Utilities.Model{Float64}();

julia> x = MOI.add_variable(model)
MOI.VariableIndex(1)

julia> MOI.add_constraint(model, x, MOI.LessThan(2.0))
MathOptInterface.ConstraintIndex{MathOptInterface.VariableIndex, MathOptInterface.LessThan{Float64}}(1)
```
