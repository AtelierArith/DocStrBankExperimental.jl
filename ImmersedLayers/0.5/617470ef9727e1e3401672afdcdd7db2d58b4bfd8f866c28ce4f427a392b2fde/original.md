```
SurfaceScalarCache(X::VectorData,g::PhysicalGrid[,ddftype=CartesianGrids.Yang3][,scaling=GridScaling])
```

Create a cache of type `BasicILMCache`, holding operators and storage data for use in immersed layer operations on scalar data. The `X` specifies the is assumed to hold the endpoints of the immersed surface segments, and `g` the physical grid.
