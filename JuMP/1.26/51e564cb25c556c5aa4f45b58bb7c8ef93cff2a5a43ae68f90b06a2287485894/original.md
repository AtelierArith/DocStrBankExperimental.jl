```
struct ConstraintNotOwned{C<:ConstraintRef} <: Exception
    constraint_ref::C
end
```

An error thrown when the constraint `constraint_ref` was used in a model different to `owner_model(constraint_ref)`.

## Example

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
