```
struct ConstraintNotOwned{C<:ConstraintRef} <: Exception
    constraint_ref::C
end
```

`constraint_ref`が`owner_model(constraint_ref)`とは異なるモデルで使用されたときにスローされるエラーです。

## 例

```jldoctest
julia> model = Model();

julia> @variable(model, x);

julia> @constraint(model, c, x >= 0)
c : x ≥ 0

julia> model_new = Model();

julia> MOI.get(model_new, MOI.ConstraintName(), c)
ERROR: ConstraintNotOwned{ConstraintRef{Model, MathOptInterface.ConstraintIndex{MathOptInterface.ScalarAffineFunction{Float64}, MathOptInterface.GreaterThan{Float64}}, ScalarShape}}(c : x ≥ 0)
Stacktrace:
[...]
```
