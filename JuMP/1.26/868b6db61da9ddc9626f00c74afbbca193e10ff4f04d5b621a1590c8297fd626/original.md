```
constraint_object(con_ref::ConstraintRef)
```

Return the underlying constraint data for the constraint referenced by `con_ref`.

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

A vector constraint:

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
```
