```
struct SymMatrix{T} <: AbstractMatrix{T}
    Q::Vector{T}
    n::Int
end
```

Symmetric $n \times n$ matrix storing the vectorized upper triangular part of the matrix in the `Q` vector (this corresponds to the vectorized form of `MathOptInterface.PositiveSemidefiniteConeTriangle`). It implement the `AbstractMatrix` interface except for `setindex!` as it might break its symmetry. The [`symmetric_setindex!`](@ref) function should be used instead.
