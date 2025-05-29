```
SkewSymMatrix(A::AbstractMatrix)
```

Perform `0.5 * (A - A')` and store the matrix in an efficient way (as a vector with $n(n-1)/2$ entries).

If the constructor is called with a matrix as input it returns a skew-symmetric matrix via the projection:

$$
A \mapsto \frac{1}{2}(A - A^T).
$$

# Examples

```jldoctest
using GeometricMachineLearning
M = [1 2 3 4; 5 6 7 8; 9 10 11 12; 13 14 15 16]
SkewSymMatrix(M)

# output

4×4 SkewSymMatrix{Float64, Vector{Float64}}:
 0.0  -1.5  -3.0  -4.5
 1.5   0.0  -1.5  -3.0
 3.0   1.5   0.0  -1.5
 4.5   3.0   1.5   0.0
```

# Extended help

Note that the constructor is designed in such a way that it always returns matrices of type `SkewSymMatrix{<:AbstractFloat}` when called with a matrix, even if this matrix is of type `AbstractMatrix{<:Integer}`.

If the user wishes to allocate a matrix `SkewSymMatrix{<:Integer}` then call:

```julia
SkewSymMatrix(::AbstractVector, n::Integer)
```

Note that this is different from [`LowerTriangular`](@ref) and [`UpperTriangular`](@ref) as no porjection takes place there.
