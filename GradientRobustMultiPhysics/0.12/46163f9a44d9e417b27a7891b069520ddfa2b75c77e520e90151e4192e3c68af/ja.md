```julia
abstract type CorrectDirichletBoundary{id} <: GradientRobustMultiPhysics.DirichletBoundary
```

指定されたidの境界データを修正し、両方の未知数の合計の区分的積分平均が保持されるようにします。
