```
DistanceGradient <: NeutralLandscapeMaker

DistanceGradient(; sources=[1])
DistanceGradient(sources)
```

`sources` フィールドは、距離を計算する必要がある行列の *線形* インデックスの `Vector{Integer}` です。
