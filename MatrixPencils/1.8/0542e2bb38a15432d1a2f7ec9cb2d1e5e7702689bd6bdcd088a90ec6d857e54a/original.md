```
ordeigvals(A, B) -> (ev, α, β)
```

Compute the vector `ev` of generalized eigenvalues of the pair `(A,B)`, with `A` a Schur matrix and `B` an upper triangular matrix,  in their order of appearance down the diagonals of `A` and `B`. `ordeigvals` is an order-preserving version of `eigvals` for (triangular/quasi-upper-triangular, triangular) pairs of matrices. `α` is a complex vector and `β` is a real vector such that the generalized eigenvalues `ev` can be alternatively obtained with `α./β`.
