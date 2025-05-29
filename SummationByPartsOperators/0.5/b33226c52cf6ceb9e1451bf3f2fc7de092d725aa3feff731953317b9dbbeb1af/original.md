```
MultidimensionalMatrixDerivativeOperator{Dim, T}
MultidimensionalMatrixDerivativeOperator(nodes::NodesType, boundary_indices::Vector{Int}, normals::Vector{SVector{Dim,T}},
                                         weights::Vector{T}, weights_boundary::Vector{T}, Ds::NTuple{Dim,DType},
                                         accuracy_order::Int, source::SourceOfCoefficients) where {Dim,T<:Real,NodesType,DType<:AbstractMatrix{T}}
```

Multidimensional operator that represents a first-derivative operator based on matrices.

An instance of this type can be constructed by passing the nodes `nodes` (e.g. a `Vector{SVector}`), a vector of indices `boundary_indices` that indicates which nodes are on the boundary, the normal vectors `normals` of the boundary nodes, the weights `weights` and `weights_boundary` of the operator, the derivative matrices `Ds` in each direction, the `accuracy_order` of the operator, and the `source` of coefficients, which can be `nothing` for experimentation. The lengths of `boundary_indices`, `normals`, and `weights_boundary` should be the same and should coincide with the number of boundary nodes. Indices in `boundary_indices` can appear multiple times if the boundary nodes are shared between different boundaries, e.g. corners.

To obtain the derivative operator in a specific direction, use `D[dim]`. The boundary operator in a specific direction can be obtained with `mass_matrix_boundary(D, dim)` and will be constructed as a mimetic operator based on `weights_boundary`. The mass matrix of the operator is given by `mass_matrix(D)`.

See also [`TensorProductOperator`](@ref).

References:

  * Jason E. Hicken, David C. Del Rey Fernandez, and David W. Zingg (2016) Multidimensional Summation-by-Parts Operators: General Theory and Application to Simplex Elements SIAM Journal of Scientific Computing 38(4), pp. A1935-A1958, [DOI: 10.1137/15M1038360](https://doi.org/10.1137/15M1038360).
  * Jan Glaubitz, Simon-Christian Klein, Jan Nordström, Philipp Öffner (2023) Multi-dimensional summation-by-parts operators for general function spaces: Theory and construction Journal of Computational Physics 491, 112370, [DOI: 10.1016/j.jcp.2023.112370](https://doi.org/10.1016/j.jcp.2023.112370).
