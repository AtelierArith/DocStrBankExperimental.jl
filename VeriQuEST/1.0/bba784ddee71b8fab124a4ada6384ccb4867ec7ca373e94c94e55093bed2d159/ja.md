```
mutable struct QubitNoiseParameters <: NoiseParameters
```

量子システムのためのキュービットノイズパラメータ。

# フィールド

  * `ρ::Union{DensityMatrix,Qureg}`: キュービットの状態を表す密度行列または量子レジスタ。
  * `q::Union{Nothing,Vector{Int64},Int64,Vector{Int32},Int32}`: ノイズの影響を受けるキュービットのインデックス。
