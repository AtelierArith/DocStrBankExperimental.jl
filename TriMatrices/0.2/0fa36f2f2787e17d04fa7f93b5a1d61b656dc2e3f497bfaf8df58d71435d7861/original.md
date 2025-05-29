```julia
struct TriLower{D} <: TriMatrices.TriLayout{D}
```

The lower triangle of the matrix is stored, values above the diagonal are zero.
