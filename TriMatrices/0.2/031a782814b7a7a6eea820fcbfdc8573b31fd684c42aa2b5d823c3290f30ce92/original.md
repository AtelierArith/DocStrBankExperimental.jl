```julia
struct TriSymmetric{D} <: TriMatrices.TriLayout{D}
```

Matrix is symmetric across the diagonal, one value is stored for each pair of non-diagonal entries.
