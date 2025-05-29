```
fflu(A::MatrixElem{T}, P = SymmetricGroup(nrows(A))) where {T <: RingElement}
```

Return a tuple $r, d, p, L, U$ consisting of the rank of $A$, a denominator $d$, a permutation $p$ of $A$ belonging to $P$, a lower triangular matrix $L$ and an upper triangular matrix $U$ such that $p(A) = LDU$, where $p(A)$ stands for the matrix whose rows are the given permutation $p$ of the rows of $A$ and such that $D$ is the diagonal matrix diag$(p_1, p_1p_2, \ldots, p_{n-2}p_{n-1}, p_{n-1}p_n)$ where the $p_i$ are the inverses of the diagonal entries of $L$. The denominator $d$ is set to $\pm \mathrm{det}(S)$ where $S$ is an appropriate submatrix of $A$ ($S = A$ if $A$ is square and nonsingular) and the sign is decided by the parity of the permutation.
