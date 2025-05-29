```
RecombineMatrix{T} <: AbstractMatrix{T}
```

Matrix for transformation from coefficients of the recombined basis, to the corresponding B-spline basis coefficients.

# Extended help

The transformation matrix $M$ is defined by

$$
ϕ_j = M_{ij} b_i,
$$

where $b_j(x)$ and $ϕ_i(x)$ are elements of the B-spline and recombined bases, respectively.

This matrix allows to pass from known coefficients $u_j$ in the recombined basis $ϕ_j$, to the respective coefficients $v_i$ in the B-spline basis $b_i$:

$$
\bm{v} = \mathbf{M} \bm{u}.
$$

Note that the matrix is not square: it has dimensions $N × M$, where $N$ is the length of the B-spline basis, and $M = N - δ$ is that of the recombined basis (see [`RecombinedBSplineBasis`](@ref) for details).

Due to the local support of B-splines, basis recombination can be performed by combining just a small set of B-splines near the boundaries (as discussed in [`RecombinedBSplineBasis`](@ref)). This leads to a recombination matrix which is almost a diagonal of ones, plus a few extra super- and sub-diagonal elements in the upper left and lower right corners, respectively. The matrix is stored in a memory-efficient way that also allows fast access to its elements.

Efficient implementations of matrix-vector products (using the `*` operator or `LinearAlgebra.mul!`) and of left division of vectors (using `\` or `LinearAlgebra.ldiv!`) are included. These two operations can be used to transform between coefficients in the original and recombined bases.

Note that, since the recombined basis forms a subspace of the original basis (which is related to the rectangular shape of the matrix), it is generally not possible to obtain recombined coefficients from original coefficients, unless the latter already satisfy the constraints encoded in the recombined basis. The left division operation will throw a [`NoUniqueSolutionError`](@ref) if that is not the case.

---

```
RecombineMatrix(ops::Tuple{Vararg{AbstractDifferentialOp}}, B::BSplineBasis, [T])
RecombineMatrix(ops_left, ops_right, B::BSplineBasis, [T])
```

Construct recombination matrix describing a B-spline basis recombination.

In the first case, `ops` is the boundary condition (BC) to be applied on both boundaries. The second case allows to set different BCs on each boundary.

The default element type `T` is generally `Float64`, except for specific differential operators which yield a matrix of zeroes and ones, for which `Bool` is the default.

See the [`RecombinedBSplineBasis`](@ref) constructor for details on the `ops` argument.
