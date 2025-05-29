```julia
function closest_pair(a::AbstractShape{2}, b::AbstractShape{2}, state::State{R})
```

Given two shapes `a` and `b` and a `state` describing the position and rotation of `b` relative to `a`, return the points on the boundary of `a` and `b` respectively which are closest to each other. Only valid for shapes that do not intersect.
