```julia
abstract type AbstractVectorILMProblem{DT, ST, DTP} <: ImmersedLayers.AbstractILMProblem{DT, ST, DTP}
```

ベクトルデータを持つ問題タイプを定義する際は、これのサブタイプにしてください。
