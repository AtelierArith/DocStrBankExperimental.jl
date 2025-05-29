```
unconstrained_nlp(solver; problem_set = unconstrained_nlp_set(), atol = 1e-6, rtol = 1e-6)
```

Test the `solver` on unconstrained problems. If `rtol` is non-zero, the relative error uses the gradient at the initial guess.
