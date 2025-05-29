```
entropy(P::AbstractArray; [dims])
```

Computes the joint entropy of a probability matrix. Does not perform any checks whether the matrix is normalized. Output in bits.

If the `dims` keyword argument is provided, the marginal entropy of the matrix is computed. `dims` indicates whether to compute the entropy for the rows  (`dims=1`) or columns (`dims=2`).
