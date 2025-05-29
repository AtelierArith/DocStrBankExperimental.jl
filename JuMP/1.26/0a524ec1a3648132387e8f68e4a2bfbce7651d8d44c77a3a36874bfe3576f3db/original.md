```
index(cr::ConstraintRef)::MOI.ConstraintIndex
```

Return the index of the constraint that corresponds to `cr` in the MOI backend.

## Example

```jldoctest
julia> model = Model();

julia> @variable(model, x);

julia> @constraint(model, c, x >= 0);

julia> index(c)
MathOptInterface.ConstraintIndex{MathOptInterface.ScalarAffineFunction{Float64}, MathOptInterface.GreaterThan{Float64}}(1)
```
