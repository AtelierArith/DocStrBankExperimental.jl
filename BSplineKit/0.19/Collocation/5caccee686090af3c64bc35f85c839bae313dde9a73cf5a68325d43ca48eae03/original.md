```
collocation_matrix(
    B::AbstractBSplineBasis,
    x::AbstractVector,
    [deriv::Derivative = Derivative(0)],
    [MatrixType = CollocationMatrix{Float64}];
    clip_threshold = eps(eltype(MatrixType)),
)
```

Return collocation matrix mapping B-spline coefficients to spline values at the collocation points `x`.

# Extended help

The matrix elements are given by the B-splines evaluated at the collocation points:

$$
C_{ij} = b_j(x_i) \quad \text{for} \quad
i ∈ [1, N_x] \text{ and } j ∈ [1, N_b],
$$

where `Nx = length(x)` is the number of collocation points, and `Nb = length(B)` is the number of B-splines in `B`.

To obtain a matrix associated to the B-spline derivatives, set the `deriv` argument to the order of the derivative.

Given the B-spline coefficients $\{u_j, 1 ≤ j ≤ N_b\}$, one can recover the values (or derivatives) of the spline at the collocation points as `v = C * u`. Conversely, if one knows the values $v_i$ at the collocation points, the coefficients $u$ of the spline passing by the collocation points may be obtained by inversion of the linear system `u = C \ v`.

The `clip_threshold` argument allows one to ignore spurious, negligible values obtained when evaluating B-splines. These values are typically unwanted, as they artificially increase the number of elements (and sometimes the bandwidth) of the matrix. They may appear when a collocation point is located on a knot. By default, `clip_threshold` is set to the machine epsilon associated to the matrix element type (see `eps` in the Julia documentation). Set it to zero to disable this behaviour.

## Matrix types

The `MatrixType` optional argument allows to select the type of returned matrix.

Due to the compact support of B-splines, the collocation matrix is [banded](https://en.wikipedia.org/wiki/Band_matrix) if the collocation points are properly distributed.

### Supported matrix types

  * `CollocationMatrix{T}`: similar to a `BandedMatrix{T}`, with efficient LU factorisations without pivoting (see [`CollocationMatrix`](@ref) for details). This option performs much better than sparse matrices for inversion of linear systems. On the other hand, for matrix-vector or matrix-matrix multiplications, `SparseMatrixCSC` may perform better, especially when using OpenBLAS (see [BandedMatrices issue](https://github.com/JuliaLinearAlgebra/BandedMatrices.jl/issues/110)). May fail with an error for non-square matrix shapes, or if the distribution of collocation points is not adapted. In these cases, the effective bandwidth of the matrix may be larger than the expected bandwidth.
  * `SparseMatrixCSC{T}`: regular sparse matrix; correctly handles all matrix shapes.
  * `Matrix{T}`: a regular dense matrix. Generally performs worse than the alternatives, especially for large problems.

!!! note "Periodic B-spline bases"
    The default matrix type is `CollocationMatrix{T}`, *except* for periodic bases ([`PeriodicBSplineBasis`](@ref)), in which case the collocation matrix has a few out-of-bands entries due to periodicity. For *cubic* periodic bases, the [`Collocation.CyclicTridiagonalMatrix`](@ref) matrix type is used, which implements efficient solution of linear problems. For non-cubic periodic bases, `SparseMatrixCSC` is the default. Note that this may change in the future.


See also [`collocation_matrix!`](@ref).
