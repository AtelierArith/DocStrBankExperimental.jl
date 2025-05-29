```
shape(c::AbstractConstraint)::AbstractShape
```

Return the shape of the constraint `c`.

## Example

```jldoctest
julia> model = Model();

julia> @variable(model, x[1:2]);

julia> c = @constraint(model, x[2] <= 1);

julia> shape(constraint_object(c))
ScalarShape()

julia> d = @constraint(model, x in SOS1());

julia> shape(constraint_object(d))
VectorShape()
```
