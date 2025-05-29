```
entropy(N::AbstractEcologicalNetwork; [dims])
```

Computes the joint entropy of an ecological network. If `dims` is specified, The marginal entropy of the ecological network is computed. `dims` indicates whether to compute the entropy for the rows (`dims=1`) or columns (`dims=2`). Output in bits.
