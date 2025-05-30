```julia
abstract type ReconstructionNormalFlux{FEreconst<:GradientRobustMultiPhysics.AbstractFiniteElement} <: ??
```

再構成法則フラックス: 再構成された有限要素関数の法則フラックスを評価します。

FEreconstは、適用される有限要素に対して定義されている場合、再構成空間と再構成アルゴリズムを指定します。
