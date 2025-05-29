```julia
struct CombineDofs{T} <: GradientRobustMultiPhysics.AbstractGlobalConstraint
```

指定された自由度を2つの未知数（同じでも可）に結合し、異なる領域や周期境界条件で異なる未知数を接続できるようにします。
