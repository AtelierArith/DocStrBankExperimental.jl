```
removehredundancy(hr::HRepresentation, solver)
```

Return a H-representation of the polyhedron represented by `hr` with all the elements of `hr` except the redundant ones, i.e. the elements that can be expressed as convex combination of other ones.
