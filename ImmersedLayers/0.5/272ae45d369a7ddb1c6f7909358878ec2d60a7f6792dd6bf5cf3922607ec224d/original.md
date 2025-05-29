```
SurfaceScalarCache(body::Body/BodyList,g::PhysicalGrid[,ddftype=CartesianGrids.Yang3][,scaling=GridScaling])
```

Create a cache of type `BasicILMCache`, holding operators and storage data for use in immersed layer operations on scalar data. This is sometimes called from within`ILMSystem` rather than directly.

The `body` can be of type `Body` or `BodyList`. The keyword `scaling` can be used to set the scaling in the operations. By default, it is set to `IndexScaling` which sets the regularization and interpolation to be symmetric matrices (i.e., interpolation is the adjoint of regularization with   respect to a vector dot product), and the vector calculus operations on the grid   are simple differences. By using `scaling = GridScaling`, then the grid and   point spacings are accounted for. Interpolation and regularization are adjoints   with respect to inner products based on discretized surface and volume integrals,   and vector calculus operations are scaled by the grid spacing.
