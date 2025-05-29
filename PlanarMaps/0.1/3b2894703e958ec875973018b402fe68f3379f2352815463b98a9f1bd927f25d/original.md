```
face(P::PlanarMap,u::Int64,v::Int64,rotate=cw)
```

Return the face of the planar map P which includes the edge (u,v) and finds each new edge by rotating in the specified direction about the current vertex. Note that this traces out the face in the direction *opposite* to `rotate`
