```
ptrace(rho::AbstractMatrix, which::Int=2)
```

Partial trace of `rho` along dimension `which`.

`rho` is split into halves and the trace is over the second half by default.
