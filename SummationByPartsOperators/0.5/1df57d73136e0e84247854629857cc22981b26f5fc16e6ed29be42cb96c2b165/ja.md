```
couple_continuously(D, mesh)
```

与えられた `mesh` のセル上での `D` の連続的なカップリングに対応する微分演算子を返します。これは（ノーダル）連続ガレルキン（CG）法におけるものです。基礎となるSBP演算子が [`LegendreDerivativeOperator`](@ref) の場合、これはCGスペクトル要素法（CGSEM）です。ただし、任意のSBP演算子の連続的なカップリングもサポートされています。

`mesh` は [`UniformMesh1D`](@ref) または [`UniformPeriodicMesh1D`](@ref) であることができます。

## 参考文献

  * Ranocha, Mitsotakis, Ketcheson (2021). A Broad Class of Conservative Numerical Methods for Dispersive Wave Equations. [DOI: 10.4208/cicp.OA-2020-0119](https://doi.org/10.4208/cicp.OA-2020-0119)
