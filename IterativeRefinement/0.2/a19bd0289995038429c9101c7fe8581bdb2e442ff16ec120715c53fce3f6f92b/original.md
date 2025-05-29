```
rfeigen(A,x,λ,DT) => λnew, xnew, status
```

Improve the precision of a computed eigenpair `(x,λ)` for matrix `A` via multi-precision iterative refinement, using more-precise real type `DT`.

The higher precision `DT` is only used for residual computation (i.e. matrix-vector products), so this can be much faster than a full eigensystem solution with precise eltype.  This method works on a single eigenpair, and can fail spectacularly if there is another eigenvalue nearby.
