```
struct KrausMapNoiseParameters <: NoiseParameters
```

`KrausMapNoiseParameters`構造体は、Krausマップノイズモデルのノイズパラメータを表します。

フィールド:

  * `trace`: Union{TracePreserving,NotTracePreserving} - ノイズがトレース保存かどうかを指定します。
  * `ρ`: Union{DensityMatrix,Qureg} - 初期状態を表す密度行列または量子レジスタ。
  * `q`: Union{Nothing,Vector{Int64},Int64,Vector{Int32},Int32} - ノイズの影響を受けるキュービットのインデックス。
  * `mat`: Matrix{ComplexF64} - Kraus演算子の行列表現。
  * `num_ops`: Union{Int32,Int64} - Kraus演算子の数。
  * `num_qubits`: Union{Nothing,Int64} - システム内のキュービットの数。
