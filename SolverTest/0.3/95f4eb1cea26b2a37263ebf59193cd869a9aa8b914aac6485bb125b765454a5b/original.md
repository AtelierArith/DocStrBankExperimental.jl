```
equality_constrained_nls(solver; problem_set = equality_constrained_nls_set(), atol = 1e-6, rtol = 1e-6)
```

Test the `solver` on equality-constrained problems. If `rtol` is non-zero, the relative error uses the gradient at the initial guess.
