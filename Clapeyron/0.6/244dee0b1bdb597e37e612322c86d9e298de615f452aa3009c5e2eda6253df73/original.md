```
set_k!(model,k)
set_k!(model,ki...)
```

Sets the model "k-values" binary interaction parameter to the input matrix `k`. If the input model requires multiple k-matrices (as is the case for T-dependent values, i.e: k(T) = k1 + k2*T), then you must call `set_k!` with all the matrices as input (`set_k!(model,k1,k2)`).
