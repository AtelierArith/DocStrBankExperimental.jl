```
struct ConstantCartesianCoriolis{FT} <: AbstractRotation
```

局所的な垂直成分と、定数回転ベクトルの局所的な水平成分の両方を考慮したコリオリの実装です。これは、局所的な垂直成分のみを考慮する[`FPlane`](@ref)のより一般的な実装です。
