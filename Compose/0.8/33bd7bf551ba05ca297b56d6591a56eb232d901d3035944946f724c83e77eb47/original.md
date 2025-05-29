```
bezigon(anchor0::Tuple, sides::Vector{<:Vector{<:Tuple}})
```

Define a bezier polygon. `anchor0` is the starting point as an `(x,y)` tuple. `sides` contains Vectors of side points (tuples): each vector has the control point(s) and end point for each side  (the end point forms the next starting point). The sides can be linear (1 point), quadratic (2 points) or cubic (3 points).
