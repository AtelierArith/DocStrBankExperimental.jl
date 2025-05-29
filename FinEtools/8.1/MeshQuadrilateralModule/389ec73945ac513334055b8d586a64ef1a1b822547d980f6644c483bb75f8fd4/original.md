```
Q4blockx(xs::Vector{T}, ys::Vector{T})
```

Graded mesh  of a rectangle, Q4 finite elements.

Mesh of a 2-D block, Q4 finite elements. The nodes are located at the Cartesian product of the two intervals on the input.  This allows for construction of graded meshes.

xs,ys - Locations of the individual planes of nodes.
