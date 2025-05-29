```
SHermitianCompact{N, T, L} <: StaticMatrix{N, N, T}
```

A [`StaticArray`](@ref) subtype that can represent a Hermitian matrix. Unlike `LinearAlgebra.Hermitian`, `SHermitianCompact` stores only the lower triangle of the matrix (as an `SVector`), and the diagonal may not be real. The lower triangle is stored in column-major order and the superdiagonal entries are  `adjoint` to the transposed subdiagonal entries. The diagonal is returned as-is. For example, for an `SHermitianCompact{3}`, the indices of the stored elements can be visualized as follows:

```
┌ 1 ⋅ ⋅ ┐
| 2 4 ⋅ |
└ 3 5 6 ┘
```

Type parameters:

  * `N`: matrix dimension;
  * `T`: element type for lower triangle;
  * `L`: length of the `SVector` storing the lower triangular elements.

Note that `L` is always the `N`th [triangular number](https://en.wikipedia.org/wiki/Triangular_number).

An `SHermitianCompact` may be constructed either:

  * from an `AbstractVector` containing the lower triangular elements; or
  * from a `Tuple` containing both upper and lower triangular elements in column major order; or
  * from another `StaticMatrix`.

For the latter two cases, only the lower triangular elements are used; the upper triangular elements are ignored.

When its element type is real, then a `SHermitianCompact` is both Hermitian and symmetric. Otherwise, to ensure that a `SHermitianCompact` matrix, `a`, is Hermitian according to `LinearAlgebra.ishermitian`, take an average with its adjoint, i.e. `(a+a')/2`, or take a Hermitian view of the data with `LinearAlgebra.Hermitian(a)`. However, the latter case is not specialized to use the compact storage.
