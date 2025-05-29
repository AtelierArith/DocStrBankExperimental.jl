```julia
struct PointEvaluator{T<:Real, Tv<:Real, Ti<:Integer, FEType<:GradientRobustMultiPhysics.AbstractFiniteElement, FEOP<:??, AT<:ExtendableGrids.AssemblyType, ACT<:GradientRobustMultiPhysics.AbstractAction}
```

structure that allows to evaluate a FEVectorBlock at arbitrary points
