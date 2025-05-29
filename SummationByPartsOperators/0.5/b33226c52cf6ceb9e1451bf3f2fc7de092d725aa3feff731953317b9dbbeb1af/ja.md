```
MultidimensionalMatrixDerivativeOperator{Dim, T}
MultidimensionalMatrixDerivativeOperator(nodes::NodesType, boundary_indices::Vector{Int}, normals::Vector{SVector{Dim,T}},
                                         weights::Vector{T}, weights_boundary::Vector{T}, Ds::NTuple{Dim,DType},
                                         accuracy_order::Int, source::SourceOfCoefficients) where {Dim,T<:Real,NodesType,DType<:AbstractMatrix{T}}
```

行列に基づく一次導関数演算子を表す多次元演算子です。

この型のインスタンスは、ノード `nodes`（例えば `Vector{SVector}`）、境界上のノードを示すインデックスのベクトル `boundary_indices`、境界ノードの法線ベクトル `normals`、演算子の重み `weights` と `weights_boundary`、各方向の導関数行列 `Ds`、演算子の `accuracy_order`、および係数の `source`（実験のために `nothing` にすることも可能）を渡すことで構築できます。`boundary_indices`、`normals`、および `weights_boundary` の長さは同じで、境界ノードの数と一致する必要があります。`boundary_indices` のインデックスは、異なる境界間で共有される境界ノードがある場合、複数回出現することがあります（例えば、コーナー）。

特定の方向の導関数演算子を取得するには、`D[dim]` を使用します。特定の方向の境界演算子は `mass_matrix_boundary(D, dim)` で取得でき、`weights_boundary` に基づく模倣演算子として構築されます。演算子の質量行列は `mass_matrix(D)` で与えられます。

[`TensorProductOperator`](@ref) も参照してください。

参考文献:

  * Jason E. Hicken, David C. Del Rey Fernandez, and David W. Zingg (2016) Multidimensional Summation-by-Parts Operators: General Theory and Application to Simplex Elements SIAM Journal of Scientific Computing 38(4), pp. A1935-A1958, [DOI: 10.1137/15M1038360](https://doi.org/10.1137/15M1038360).
  * Jan Glaubitz, Simon-Christian Klein, Jan Nordström, Philipp Öffner (2023) Multi-dimensional summation-by-parts operators for general function spaces: Theory and construction Journal of Computational Physics 491, 112370, [DOI: 10.1016/j.jcp.2023.112370](https://doi.org/10.1016/j.jcp.2023.112370).
