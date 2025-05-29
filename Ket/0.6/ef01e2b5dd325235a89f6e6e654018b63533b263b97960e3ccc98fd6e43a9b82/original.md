```
 applymap!(result::Matrix, Φ::AbstractMatrix, M::AbstractMatrix)
```

Applies the CP map given by the Choi-Jamiołkowski operator `Φ` to the matrix `M` without allocating or wrapping. In the symmetric or Hermitian cases only the upper triangular is computed. `result` must be a matrix of size `dout × dout`,  where `size(M, 1) * dout == size(Φ, 1)`.
