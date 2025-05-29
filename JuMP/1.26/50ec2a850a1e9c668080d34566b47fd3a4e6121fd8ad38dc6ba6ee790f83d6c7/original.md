```
struct ScalarConstraint
```

The data for a scalar constraint.

See also the [documentation](@ref Constraints) on JuMP's representation of constraints for more background.

## Fields

  * `.func`: field contains a JuMP object representing the function
  * `.set`: field contains the MOI set

## Example

A scalar constraint:

```jldoctest
julia> model = Model();

julia> @variable(model, x);

julia> @constraint(model, c, 2x <= 1)
c : 2 x ≤ 1

julia> object = constraint_object(c)
ScalarConstraint{AffExpr, MathOptInterface.LessThan{Float64}}(2 x, MathOptInterface.LessThan{Float64}(1.0))

julia> typeof(object)
ScalarConstraint{AffExpr, MathOptInterface.LessThan{Float64}}

julia> object.func
2 x

julia> object.set
MathOptInterface.LessThan{Float64}(1.0)
```
