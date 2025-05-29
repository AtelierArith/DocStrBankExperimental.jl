```
faces(topology, rank)
```

Return an iterator with `rank`-faces of the `topology`.

## Examples

Consider a mesh of tetrahedrons embedded in a 3D space. We can loop over all 3-faces (a.k.a. elements) or over all 2-faces to handle the interfaces (i.e. triangles) between adjacent elements:

```julia
tetrahedrons = faces(topology, 3)
triangles    = faces(topology, 2)
segments     = faces(topology, 1)
```
