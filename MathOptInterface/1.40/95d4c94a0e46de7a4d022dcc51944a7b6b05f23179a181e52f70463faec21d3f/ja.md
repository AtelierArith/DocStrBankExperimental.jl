```
EqualTo{T<:Number}(value::T)
```

単一点 $\{value\} \subseteq \mathbb{R}$ を含む集合。

## 例

```jldoctest
julia> model = MOI.Utilities.Model{Float64}();

julia> x = MOI.add_variable(model)
MOI.VariableIndex(1)

julia> MOI.add_constraint(model, x, MOI.EqualTo(2.0))
MathOptInterface.ConstraintIndex{MathOptInterface.VariableIndex, MathOptInterface.EqualTo{Float64}}(1)
```
