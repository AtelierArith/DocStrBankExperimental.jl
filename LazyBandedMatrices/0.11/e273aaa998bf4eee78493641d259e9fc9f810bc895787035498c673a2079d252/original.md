```
KronTrav(A,B,C...)
```

represents a kronecker product but where the coefficients are ordered as in `DiagTrav`. For example, `KronTrav(A,B) * DiagTrav(X)` represents the same operator as `B*X*A'`, though the bottom of the right of `X` is ignored.
