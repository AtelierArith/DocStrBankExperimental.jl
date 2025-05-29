```
LOBPCGIterator(A, largest::Bool, X, P=nothing, C=nothing) -> iterator
```

# Arguments

  * `A`: linear operator;
  * `X`: initial guess of the Ritz vectors; to be overwritten by the eigenvectors;
  * `largest`: `true` if largest eigenvalues are desired and false if smallest;
  * `P`: preconditioner of residual vectors, must overload `ldiv!`;
  * `C`: constraint to deflate the residual and solution vectors orthogonal   to a subspace; must overload `mul!`.
