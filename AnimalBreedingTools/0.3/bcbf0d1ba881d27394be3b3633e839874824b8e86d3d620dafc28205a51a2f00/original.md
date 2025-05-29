```
X = get_interaction_matrix(X1, X2)
```

Returns a design matrix for the interaction between effects. The design matrices for the two main effects (`X1` and `X2`) should be provided.    Note that this function will not check if the supplied matrices are really the design matrices - it just creats all the combination of column products among the input matrices.
