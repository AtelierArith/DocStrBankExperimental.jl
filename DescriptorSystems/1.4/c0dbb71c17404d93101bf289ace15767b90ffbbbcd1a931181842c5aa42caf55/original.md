```
sysr = dsxvarsel(sys,ind)
```

Construct for the descriptor system `sys = (A-λE,B,C,D)` of order `n` the descriptor system   `sysr = (A[ind,ind]-λE[ind,ind],B[ind,:],C[:,ind],D)` of order `nr = length(ind)`,  by selecting the state variables of `sys` with indices specified by `ind`.  If `ind` is a permutation vector of length `n`, then `sysr` has the same transfer function matrix as `sys`  and permuted state variables. 
