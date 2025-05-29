```
hybridized_SBP_operators(md::MeshData{2, <:CutCellMesh})
```

This constructs hybridized SBP operators using the approach taken in Chan (2019),  "Skew-Symmetric Entropy Stable Modal Discontinuous Galerkin Formulations".  [https://doi.org/10.1007/s10915-019-01026-w](https://doi.org/10.1007/s10915-019-01026-w)

This function returns `hybridized_operators::Vector{Tuple{<:Matrix, <:Matrix}}` and  `project_and_interp_operators, projection_operators, interpolation_operators`, which are  all `Vector{<:Matrix}`, where each entry corresponds to a cut element.
