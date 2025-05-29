```
is_real(r::PathResult; tol::Float64 = 1e-6)
```

We consider a result as `real` if the infinity-norm of the imaginary part of the solution is at most `tol`.
