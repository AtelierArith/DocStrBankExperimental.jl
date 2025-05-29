```
VolumeIntegralWeakForm()
```

DG法に関する標準的な教科書で説明されている古典的な弱形式体積積分タイプです。

## 参考文献

  * Kopriva (2009) Implementing Spectral Methods for Partial Differential Equations: Algorithms for Scientists and Engineers [doi: 10.1007/978-90-481-2261-5](https://doi.org/10.1007/978-90-481-2261-5)
  * Hesthaven, Warburton (2007) Nodal Discontinuous Galerkin Methods: Algorithms, Analysis, and Applications [doi: 10.1007/978-0-387-72067-8](https://doi.org/10.1007/978-0-387-72067-8)

`VolumeIntegralWeakForm()` は保存項に対してのみ実装されており、非保存項は常にフラックス分割スキームと併せて離散化されるべきです。詳細は [`VolumeIntegralFluxDifferencing`](@ref) を参照してください。この処理は、例えばエントロピー安定性やバランスの取れた状態を達成するために必要です。
