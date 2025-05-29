```
normalderivatives(points,normals,topology,P∇ψ,μ,∇ψ0::Function; eps=0.0001, NP=100)
```

オブジェクト表面から*内部*領域に近づく∇ψ.nを計算します。この関数を使用するには、表面の特性として`points`、`normals`、および`topology`が必要です。この関数を使用するには、接線場成分（`tangentialderivatives`および`surfacepotential`を参照）と境界ジャンプ条件μ、外部自由場の勾配が必要です。
