```
SimulationModel(g::JutulMesh, system; discretization = nothing, kwarg...)
```

シミュレーションモデルを定義する型 - 離散方程式を解くために必要なすべて。

最小限のセットアップには、トポロジーを定義する[`JutulMesh`](@ref)と、物理法則を課す[`JutulSystem`](@ref)が必要です。
