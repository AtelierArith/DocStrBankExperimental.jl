```
LowerTriangular(S::AbstractVector, n::Int)
```

Build a lower-triangular matrix from a vector.

A lower-triangular matrix is an $n\times{}n$ matrix that has zeros on the diagonal and on the upper triangular.

The data are stored in a vector $S$ similarly to other matrices. See [`UpperTriangular`](@ref), [`SkewSymMatrix`](@ref) and [`SymmetricMatrix`](@ref).

The struct two fields: `S` and `n`. The first stores all the entries of the matrix in a sparse fashion (in a vector) and the second is the dimension $n$ for $A\in\mathbb{R}^{n\times{}n}$.

# Examples

```jldoctest
using GeometricMachineLearning
S = [1, 2, 3, 4, 5, 6]
LowerTriangular(S, 4)

# output

4×4 LowerTriangular{Int64, Vector{Int64}}:
 0  0  0  0
 1  0  0  0
 2  3  0  0
 4  5  6  0
```
