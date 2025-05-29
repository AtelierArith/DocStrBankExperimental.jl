```
struct VectorConstraint
```

The data for a vector constraint.

See also the [documentation](@ref Constraints) on JuMP's representation of constraints.

## Fields

  * `func`: field contains a JuMP object representing the function
  * `set`: field contains the MOI set.
  * `shape`: field contains an [`AbstractShape`](@ref) matching the form in which the constraint was constructed (for example, by using matrices or flat vectors).

## Example

```jldoctest
julia> model = Model();

julia> @variable(model, x[1:3]);

julia> @constraint(model, c, x in SecondOrderCone())
c : [x[1], x[2], x[3]] ∈ MathOptInterface.SecondOrderCone(3)

julia> object = constraint_object(c)
VectorConstraint{VariableRef, MathOptInterface.SecondOrderCone, VectorShape}(VariableRef[x[1], x[2], x[3]], MathOptInterface.SecondOrderCone(3), VectorShape())

julia> typeof(object)
VectorConstraint{VariableRef, MathOptInterface.SecondOrderCone, VectorShape}

julia> object.func
3-element Vector{VariableRef}:
 x[1]
 x[2]
 x[3]

julia> object.set
MathOptInterface.SecondOrderCone(3)

julia> object.shape
VectorShape()
```
