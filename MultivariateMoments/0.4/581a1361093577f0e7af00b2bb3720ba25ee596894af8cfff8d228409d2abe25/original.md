```
struct VectorizedHermitianMatrix{T} <: AbstractMatrix{Complex{T}}
    Q::Vector{T}
    n::Int
end
```

Hermitian $n \times n$ matrix storing the vectorized upper triangular real part of the matrix followed by the vectorized upper triangular imaginary part in the `Q` vector (this corresponds to the vectorized form of `ComplexOptInterface.HermitianPositiveSemidefiniteConeTriangle`). It implement the `AbstractMatrix` interface except for `setindex!` as it might break its symmetry. The [`symmetric_setindex!`](@ref) function should be used instead.
