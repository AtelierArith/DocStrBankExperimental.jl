```
or!(turtle; head = Z(), up = X(), arm = Y())
```

Orient a turtle to a new direction by re-defining the local reference system. The arguments `head`, `up` and `arm` should be of type `Vec`.

## Examples

```jldoctest
julia> turtle = Turtle();

julia> using PlantGeomPrimitives

julia> or!(turtle, head = Y(), up = Z(), arm = X());
```
