```
strict_zeta_matrix(p::Poset)
```

Return the  *strict* zeta matrix of `p`. This is a (dense) 0,1-matrix whose `i,j`-entry  is `1` exactly when `p[i] < p[j]`. See also `zeta_matrix`.
