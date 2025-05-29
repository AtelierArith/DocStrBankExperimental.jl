```
ConstantBoundary(b) <: AbstractBoundaryCondition
```

Constant boundary condition type. Enforces constant boundary conditions when passed to [`SpatioTemporalEmbedding`](@ref) by filling missing out-of-bounds values in the reconstruction with parameter `b`.
