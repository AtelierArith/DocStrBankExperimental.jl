```
couple_discontinuously(D, mesh, [coupling=Val(:central)])
```

与えられた `mesh` のセル上での `D` の不連続結合に対応する導関数演算子を返します。これは（ノード）不連続ガレルキン（CG）法におけるものです。基礎となるSBP演算子が [`LegendreDerivativeOperator`](@ref) の場合、これはDGスペクトル要素法（DGSEM）です。ただし、任意のSBP演算子の不連続結合もサポートされています。

`mesh` は [`UniformMesh1D`](@ref) または [`UniformPeriodicMesh1D`](@ref) であることができます。`coupling` は次のいずれかです。

  * `Val(:central)`（デフォルト）、古典的なSBP特性をもたらします
  * `Val(:minus)` または `Val(:plus)`、アップウィンドSBP演算子をもたらします

## 参考文献

  * Ranocha, Mitsotakis, Ketcheson (2021). A Broad Class of Conservative Numerical Methods for Dispersive Wave Equations. [DOI: 10.4208/cicp.OA-2020-0119](https://doi.org/10.4208/cicp.OA-2020-0119)
