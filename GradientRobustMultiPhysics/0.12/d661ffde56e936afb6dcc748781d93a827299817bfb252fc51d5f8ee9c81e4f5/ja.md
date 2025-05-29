```julia
mutable struct AssemblyPattern{APT<:GradientRobustMultiPhysics.AssemblyPatternType, T<:Real, AT<:ExtendableGrids.AssemblyType, Tv<:Real, Ti<:Integer, ActionType<:Union{GradientRobustMultiPhysics.AbstractAction, GradientRobustMultiPhysics.AbstractNonlinearFormHandler}}
```

各アセンブリパターンは、関与する有限要素空間、演算子、および割り当てられたアクションに対して異なるアセンブリをトリガーするアセンブリパターンタイプ（APT）の1つを持っています。アセンブリタイプ（AT）は、アセンブリがセル、フェイス、エッジなどで行われるかどうかを決定します（パターンの最初の引数のアセンブリタイプに対して相対的に）。
