```
vals = jth_hess_coord!(nlp, x, j, vals)
```

Evaluate the Hessian of j-th constraint at `x` in sparse coordinate format, with `vals` of length `nlp.meta.nnzh`, in place. Only the lower triangle is returned.
