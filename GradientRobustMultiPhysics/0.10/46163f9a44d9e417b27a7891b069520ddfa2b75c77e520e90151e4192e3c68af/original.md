```julia
abstract type CorrectDirichletBoundary{id} <: GradientRobustMultiPhysics.DirichletBoundary
```

Corrects boundary data of specified id, such that piecewise integral means of the sum of both unknowns are preserved
