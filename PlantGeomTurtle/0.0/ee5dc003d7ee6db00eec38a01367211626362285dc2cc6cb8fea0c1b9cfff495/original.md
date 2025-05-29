```
set!(turtle; to = O(), head = Z(), up = X(), arm = Y())
```

Set position and orientation of a turtle. The arguments `to`, `head`, `up` and `arm` should be of type `Vec` and be passed as keyword arguments.

## Examples

```jldoctest
julia> turtle = Turtle();

julia> using PlantGeomPrimitives

julia> set!(turtle, to = O(), head = Y(), up = Z(), arm = X());
```
