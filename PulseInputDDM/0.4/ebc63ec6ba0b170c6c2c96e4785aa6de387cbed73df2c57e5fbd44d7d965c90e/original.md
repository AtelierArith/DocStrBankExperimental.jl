```
CIs(H)
```

Given a Hessian matrix `H`, compute the 2 std confidence intervals based on the Laplace approximation. If `H` is not positive definite (which it should be, but might not be due numerical round off, etc.) compute a close approximation to it by adding a correction term. The magnitude of this correction is reported.
