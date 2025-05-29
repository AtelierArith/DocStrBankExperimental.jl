```
@build_constraint(constraint_expr)
```

Constructs a `ScalarConstraint` or `VectorConstraint` using the same machinery as [`@constraint`](@ref) but without adding the constraint to a model.

Constraints using broadcast operators like `x .<= 1` are also supported and will create arrays of `ScalarConstraint` or `VectorConstraint`.

## Example

```jldoctest
julia> model = Model();

julia> @variable(model, x);

julia> @build_constraint(2x >= 1)
ScalarConstraint{AffExpr, MathOptInterface.GreaterThan{Float64}}(2 x, MathOptInterface.GreaterThan{Float64}(1.0))
```

```jldoctest
julia> model = Model();

julia> @variable(model, x[1:2]);

julia> @build_constraint(x .>= 0)
2-element Vector{ScalarConstraint{AffExpr, MathOptInterface.GreaterThan{Float64}}}:
 ScalarConstraint{AffExpr, MathOptInterface.GreaterThan{Float64}}(x[1], MathOptInterface.GreaterThan{Float64}(-0.0))
 ScalarConstraint{AffExpr, MathOptInterface.GreaterThan{Float64}}(x[2], MathOptInterface.GreaterThan{Float64}(-0.0))
```
