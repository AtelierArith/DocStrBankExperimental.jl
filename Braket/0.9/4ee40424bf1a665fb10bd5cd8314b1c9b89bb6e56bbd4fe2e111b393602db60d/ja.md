```
Braket.DensityMatrix(targets) -> Braket.DensityMatrix
Braket.DensityMatrix() -> Braket.DensityMatrix
```

`targets` に基づいて Braket.DensityMatrix を構築します。

`targets` は次のいずれかである可能性があります：

  * [`QubitSet`](@ref)
  * `Int` の `Vector` および/または [`Qubit`](@ref)
  * `Int` または `Qubit`
  * 省略した場合、測定はすべての量子ビットに適用されます。
