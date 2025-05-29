```
XPRSaddcols(prob, objcoef, mat, lb, ub)
```

Implementation of `XPRSaddcols` that combines arguments `ncols`, `ncoefs`, `start`, `rowind`, `rowcoef` into a single argument `mat`.

Note that the values in `mat.colptr` and `mat.rowval` are assumed to be 1 based indices (the function will implicitly convert them to 0 based indices for calling the C library.
