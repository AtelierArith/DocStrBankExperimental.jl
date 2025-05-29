```julia
abstract type AbstractScalarILMProblem{DT, ST, DTP} <: ImmersedLayers.AbstractILMProblem{DT, ST, DTP}
```

スカラーデータを持つ問題タイプを定義する際は、これのサブタイプにしてください。
