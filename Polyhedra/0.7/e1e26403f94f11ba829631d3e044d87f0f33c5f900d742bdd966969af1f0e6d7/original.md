```
removevredundancy(vr::VRepresentation, solver)
```

Return a V-representation of the polyhedron represented by `vr` with all the elements of `vr` except the redundant ones, i.e. the elements that can be expressed as convex combination of other ones.
