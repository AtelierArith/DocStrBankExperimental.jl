```
index(cr::ConstraintRef)::MOI.ConstraintIndex
```

`cr` に対応する制約のインデックスを MOI バックエンドから返します。

## 例

```jldoctest
julia> model = Model();

julia> @variable(model, x);

julia> @constraint(model, c, x >= 0);

julia> index(c)
MathOptInterface.ConstraintIndex{MathOptInterface.ScalarAffineFunction{Float64}, MathOptInterface.GreaterThan{Float64}}(1)
```
