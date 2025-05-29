```
hybridized_SBP_operators(md::MeshData{2, <:CutCellMesh})
```

これは、Chan (2019) のアプローチを使用してハイブリッド化されたSBP演算子を構築します。 "Skew-Symmetric Entropy Stable Modal Discontinuous Galerkin Formulations"。 [https://doi.org/10.1007/s10915-019-01026-w](https://doi.org/10.1007/s10915-019-01026-w)

この関数は `hybridized_operators::Vector{Tuple{<:Matrix, <:Matrix}}` と `project_and_interp_operators, projection_operators, interpolation_operators` を返します。これらはすべて `Vector{<:Matrix}` であり、各エントリはカット要素に対応しています。
