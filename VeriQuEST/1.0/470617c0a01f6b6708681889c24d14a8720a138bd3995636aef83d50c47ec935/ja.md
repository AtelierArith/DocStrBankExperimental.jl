```
mutable struct DensityMatrixMixtureParameters <: NoiseParameters
```

`DensityMatrixMixtureParameters`構造体は、密度行列混合ノイズモデルのパラメータを表します。これは、2つの密度行列ρ₁とρ₂を保持する可変構造体です。

# フィールド

  * `ρ₁::Union{DensityMatrix,Qureg}`: 最初の密度行列。
  * `ρ₂::Union{DensityMatrix,Qureg}`: 2番目の密度行列。
