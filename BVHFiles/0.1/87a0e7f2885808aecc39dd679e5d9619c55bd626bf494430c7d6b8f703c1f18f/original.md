```
squared_errors(g::BVHGraph, f::Integer)
```

Calculate the sum of the squared differences between the current and stored positions  of the vertices for a given frame `f`.

Only those vertices are taken into account that have got positions for every frame.

See also: [`total_squared_errors`](@ref)
