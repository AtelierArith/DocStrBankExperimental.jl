```julia
struct TriUpper{D} <: TriMatrices.TriLayout{D}
```

The upper triangle of the matrix is stored, values beneath the diagonal are zero.
