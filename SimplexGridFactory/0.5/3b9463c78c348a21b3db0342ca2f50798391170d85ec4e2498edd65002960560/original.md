```
facet!(builder,i1)
facet!(builder,i1,i2)
facet!(builder,i1,i2,i3,i4)
facet!(builder,vector_or_tuple)
facet!(builder, (x1,y1), (x2,y2))
facet!(builder, (x1,y1,z1), (x2,y2,z2),(x3,y3,z3))
```

Add a facet via the corresponding point indices returned by [`point!`](@ref). 

Facets of two points are solely used for 2D grids. Facets with more than two poins are used for 3D grids and must be  planar.
