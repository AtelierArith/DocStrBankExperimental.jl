```
billiard_vertices(v, type = FiniteWall)
```

Construct a polygon billiard that connects the given vertices `v` (vector of 2-vectors). The vertices should construct a billiard in a counter-clockwise orientation (i.e. the normal vector always points to the left of `v[i+1] - v[i]`.).

`type` decides what kind of walls to use. Ths function assumes that the first entry of `v` should be connected with the last.
