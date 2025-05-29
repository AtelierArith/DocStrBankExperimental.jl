```
GeneratedField(d::GridData,field::AbstractSpatialField...,grid::PhysicalGrid)
```

Create an instance of a spatial field function `field` on scalar grid data `d`, based on a grid `grid`. After creating the instance `g = GeneratedField(d,field,grid)`, then the resulting grid data can be accessed by typing `g()`. For vector grid data, a separate `field` must be supplied for each component.

If the fields are time dependent, then you can also evaluate `g(t)` at the desired time. The time argument is ignored if the fields are static.
