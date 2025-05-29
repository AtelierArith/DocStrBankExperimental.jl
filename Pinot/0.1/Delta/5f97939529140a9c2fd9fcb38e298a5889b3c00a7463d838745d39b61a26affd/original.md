```
transform_position(ops::Vector{Range}, pos) -> Int
```

Returns a new value for position after applying the changes described by `ops`. We move the position to the right of an insert.

```julia
julia> Pinot.transform_position([retain(1), insert("a")], 1) == 2
true
```
