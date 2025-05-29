```
SymmetricMatrix(A::AbstractMatrix)
```

Perform a projection and store the matrix in an efficient way (as a vector with $n(n+1)/2$ entries).

If the constructor is called with a matrix as input it returns a symmetric matrix via the *projection*:

$$
A \mapsto \frac{1}{2}(A + A^T).
$$

# Examples

```jldoctest
using GeometricMachineLearning
M = [1 2 3 4; 5 6 7 8; 9 10 11 12; 13 14 15 16]
SymmetricMatrix(M)

# output

4×4 SymmetricMatrix{Float64, Vector{Float64}}:
 1.0   3.5   6.0   8.5
 3.5   6.0   8.5  11.0
 6.0   8.5  11.0  13.5
 8.5  11.0  13.5  16.0
```

# Extended help

Note that the constructor is designed in such a way that it always returns matrices of type `SymmetricMatrix{<:AbstractFloat}` when called with a matrix, even if this matrix is of type `AbstractMatrix{<:Integer}`.

If the user wishes to allocate a matrix `SymmetricMatrix{<:Integer}` then call

$julia SymmetricMatrix(::AbstractVector, n::Integer)$`

Note that this is different from [`LowerTriangular`](@ref) and [`UpperTriangular`](@ref) as no porjection takes place there.
