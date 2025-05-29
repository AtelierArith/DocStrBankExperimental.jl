```
cell_parameters(cell::Cell)
```

Return `((lengths, angles), mat)` where `mat` is the matrix of the cell in upper triangular format, `lengths` is the triplet `(a, b, c)` of lengths of the three axes, and `angles` is the triplet `(α, β, γ)` of angles between them.
