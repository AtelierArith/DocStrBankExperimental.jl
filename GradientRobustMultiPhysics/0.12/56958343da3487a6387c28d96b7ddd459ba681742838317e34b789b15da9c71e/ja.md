```julia
mutable struct BoundaryData{BDT<:GradientRobustMultiPhysics.AbstractBoundaryType, MType, FType}
```

システムのコンポーネントの境界データを収集し、これまでのところDirichletBoundaryタイプのみ（上記参照）について各境界領域のAbstractBoundaryTypeを指定することを可能にします。
