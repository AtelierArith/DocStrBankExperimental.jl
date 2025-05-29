```
UpperTriangular(S::AbstractVector, n::Int)
```

Build an upper-triangular matrix from a vector.

An upper-triangular matrix is an $n\times{}n$ matrix that has zeros on the diagonal and on the lower triangular.

The data are stored in a vector $S$ similarly to other matrices. See [`LowerTriangular`](@ref), [`SkewSymMatrix`](@ref) and [`SymmetricMatrix`](@ref).

The struct two fields: `S` and `n`. The first stores all the entries of the matrix in a sparse fashion (in a vector) and the second is the dimension $n$ for $A\in\mathbb{R}^{n\times{}n}$.

# Examples

```jldoctest
using GeometricMachineLearning
S = [1, 2, 3, 4, 5, 6]
UpperTriangular(S, 4)

# output

4×4 UpperTriangular{Int64, Vector{Int64}}:
 0  1  2  4
 0  0  3  5
 0  0  0  6
 0  0  0  0
```
