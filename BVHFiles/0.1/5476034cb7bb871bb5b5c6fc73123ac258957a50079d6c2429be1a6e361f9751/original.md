```
total_squared_errors(g::BVHGraph)
```

Calculate the sum of the squared differences between the current and stored positions  of the vertices for all frames.

Only those vertices are taken into account that have got positions for every frame.

See also: [`squared_errors`](@ref)
