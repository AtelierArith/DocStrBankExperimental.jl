```
VectorShape()
```

An [`AbstractShape`](@ref) that represents vector-valued constraints.

## Example

```jldoctest
julia> model = Model();

julia> @variable(model, x[1:2]);

julia> c = @constraint(model, x in SOS1());

julia> shape(constraint_object(c))
VectorShape()
```
