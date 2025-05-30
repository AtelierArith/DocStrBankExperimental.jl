```
DensityMatrixSimulator([::T], qubit_count::Int, shots::Int) -> DensityMatrixSimulator{T, Matrix{T}}
```

`2^qubit_count x 2^qubit_count` 要素を持つ `DensityMatrixSimulator` を作成し、測定するための `shots` ショットを指定します。デフォルトの要素タイプは `ComplexF64` です。
