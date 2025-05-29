```
trred_matrix(O::AlgAssAbsOrd) -> ZZMatrix
```

Returns the reduced trace matrix $M$ of $O$, i. e. `M[i, j] = trred(b[i]*b[j])`, where $b$ is a basis of $O$.
