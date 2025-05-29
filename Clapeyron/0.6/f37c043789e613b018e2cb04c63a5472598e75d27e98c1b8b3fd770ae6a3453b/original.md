```
set_l!(model,l)
set_l!(model,li...)
```

Sets the model "l-values" binary interaction parameter to the input matrix `l`. If the input model requires multiple l-matrices (as is the case for T-dependent values, i.e: l(T) = l1 + l2*T), then you must call `set_l!` with all the matrices as input (`set_l!(model,l1,l2)`).
