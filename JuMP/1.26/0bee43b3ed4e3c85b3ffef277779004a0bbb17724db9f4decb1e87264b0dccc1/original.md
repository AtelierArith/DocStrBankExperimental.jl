```
ArrayShape{N}(dims::NTuple{N,Int}) where {N}
```

An [`AbstractShape`](@ref) that represents array-valued constraints.

## Example

```jldoctest
julia> model = Model();

julia> @variable(model, x[1:2, 1:3]);

julia> c = @constraint(model, x >= 0, Nonnegatives())
[x[1,1]  x[1,2]  x[1,3]
 x[2,1]  x[2,2]  x[2,3]] ∈ Nonnegatives()

julia> shape(constraint_object(c))
ArrayShape{2}((2, 3))
```
