```
onehot(mat::AbstractMatrix) -> Matrix{Float64}
```

Each column of an input matrix represents a single categorical vector. Onehot-encode the individual columns and horizontally concatenate them as an output.
