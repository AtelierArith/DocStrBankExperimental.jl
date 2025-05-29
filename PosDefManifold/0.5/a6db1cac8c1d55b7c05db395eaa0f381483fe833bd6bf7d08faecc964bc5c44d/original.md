```
(1) sumOfSqr(A::Array)
(2) sumOfSqr(H::ℍ{T})
(3) sumOfSqr(L::𝕃{T})
(4) sumOfSqr(D::𝔻{T})
(5) sumOfSqr(X::Union{𝕄{T}, ℍ{T}}, j::Int)
(6) sumOfSqr(X::Union{𝕄{T}, ℍ{T}}, range::UnitRange)
for (1)-(6) above: where T<:RealOrComplex
```

**alias**: `ss`

Return

  * (1) the sum of squares of the elements in an array $A$ of any dimensions.
  * (2) as in (1), but for an `Hermitian` matrix $H$, using only the lower triangular part.
  * (3) as in (1), but for a `LowerTriangular` matrix $L$.
  * (4) as in (1), but for a `Diagonal` matrix $D$ (sum of squares of diagonal elements).
  * (5) the sum of square of the $j^{th}$ column of a `Matrix` or `Hermitian` $X$.
  * (6) the sum of square of the columns of a `Matrix` or `Hermitian` $X$ in a given range.

All methods support real and complex matrices.

Only method (1) works for arrays of any dimensions.

Methods (1)-(4) return the square of the [Frobenius norm](https://bit.ly/2Fi10eH).

For method (5), $j$ is a positive integer in range `1:size(X, 1)`.

For method (6), $range$ is a [UnitRange type](https://bit.ly/2HDoFbk).

**See also**: [`colNorm`](@ref), [`sumOfSqrDiag`](@ref), [`sumOfSqrTril`](@ref).

**Examples**

```julia
using PosDefManifold
X=randn(10, 20)
sum2=sumOfSqr(X)        # (1) sum of squares of all elements
sum2=sumOfSqr(X, 1)     # (2) sum of squares of elements in column 1
sum2=sumOfSqr(X, 2:4)   # (3) sum of squares of elements in column 2 to 4
```
