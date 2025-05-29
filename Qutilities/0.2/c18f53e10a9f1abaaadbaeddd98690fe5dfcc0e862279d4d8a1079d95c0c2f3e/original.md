```
ptranspose(rho::AbstractMatrix, which::Int=2)
```

Partial transpose of `rho` along dimension `which`.

`rho` is split into halves and the transpose is over the second half by default.
