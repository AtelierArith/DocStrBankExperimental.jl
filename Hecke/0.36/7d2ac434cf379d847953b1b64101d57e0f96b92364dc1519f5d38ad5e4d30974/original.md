```
minkowski_matrix(O::AbsNumFieldOrder, abs_tol::Int = 64) -> ArbMatrix
```

Returns the Minkowski matrix of $\mathcal O$.  Thus if $\mathcal O$ has degree $d$, then the result is a matrix in $\operatorname{Mat}_{d\times d}(\mathbf R)$. The entries of the matrix are real balls of type `ArbFieldElem` with radius less then `2^-abs_tol`.
