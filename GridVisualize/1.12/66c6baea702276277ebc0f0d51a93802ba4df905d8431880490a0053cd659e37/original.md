```
      vectorsample(grid::ExtendableGrid{Tv, Ti}, v;
                  offset = :default,
                  rasterpoints = 15,
                  reltol = 1.0e-10,
                  gridscale = 1.0,
                  xlimits = (1, -1),
                  ylimits = (1, -1),
                  zlimits = (1, -1)) where {Tv, Ti}
```

Extract values of given vector field (either nodal values of a piecewise linear vector field or a callback function providing evaluation of the vector field for given generalized barycentric coordinates). at all sampling points on  `offset+ i*spacing` for i in Z^d  defined by the tuples offset and spacing. Returned values can be fed into [`quiverdata`](@ref)

By default, offset is at the minimum of grid coordinates, and spacing is defined the largest grid extend divided by 10.

The intermediate `rasterflux` in future versions can be used to calculate streamlines.

The code is 3D ready.
