```
@build_constraint(constraint_expr)
```

Constructs a `ScalarConstraint` or `VectorConstraint` using the same machinery as [`@constraint`](@ref) but without adding the constraint to a model.

Constraints using broadcast operators like `x .<= 1` are also supported and will create arrays of `ScalarConstraint` or `VectorConstraint`.

## Examples

```jldoctest; setup = :(using JuMP)
model = Model();
@variable(model, x);
@build_constraint(2x >= 1)

# output
ScalarConstraint{GenericAffExpr{Float64,VariableRef},MathOptInterface.GreaterThan{Float64}}(2 x, MathOptInterface.GreaterThan{Float64}(1.0))
```
