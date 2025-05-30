```julia
struct PointEvaluator{T<:Real, Tv<:Real, Ti<:Integer, FEType<:GradientRobustMultiPhysics.AbstractFiniteElement, FEOP<:??, AT<:ExtendableGrids.AssemblyType, ACT<:GradientRobustMultiPhysics.AbstractAction}
```

任意の点でFEVectorBlockを評価することを可能にする構造体
