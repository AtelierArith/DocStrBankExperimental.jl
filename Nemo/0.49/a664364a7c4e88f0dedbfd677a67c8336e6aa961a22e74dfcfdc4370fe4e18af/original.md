```
eigenvalues_with_multiplicities(A::AcbMatrix)
```

Return the eigenvalues of `A` with their algebraic multiplicities as a vector of tuples `(AcbFieldElem, Int)`. Each tuple `(z, k)` corresponds to a cluster of `k` eigenvalues of $A$.

This function is experimental.
