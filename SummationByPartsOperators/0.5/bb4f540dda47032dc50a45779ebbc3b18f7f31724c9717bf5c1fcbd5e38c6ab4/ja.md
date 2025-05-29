```
mass_matrix_boundary(D::AbstractMultidimensionalMatrixDerivativeOperator, dim)
```

[`MultidimensionalMatrixDerivativeOperator`](@ref) `D`の方向`dim`における境界の質量行列を構築します。境界質量行列は模倣的に構築されます。詳細は以下を参照してください。

  * Jan Glaubitz, Simon-Christian Klein, Jan Nordström, Philipp Öffner (2023) Multi-dimensional summation-by-parts operators for general function spaces: Theory and construction Journal of Computational Physics 491, 112370, [DOI: 10.1016/j.jcp.2023.112370](https://doi.org/10.1016/j.jcp.2023.112370).

```
