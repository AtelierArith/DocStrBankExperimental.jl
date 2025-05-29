```
ScalarShape()
```

An [`AbstractShape`](@ref) that represents scalar constraints.

## Example

```jldoctest
julia> model = Model();

julia> @variable(model, x[1:2]);

julia> c = @constraint(model, x[2] <= 1);

julia> shape(constraint_object(c))
ScalarShape()
```
