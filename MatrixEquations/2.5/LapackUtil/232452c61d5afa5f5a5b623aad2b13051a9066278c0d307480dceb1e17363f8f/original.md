```
lacn2!(V, X, ISGN, EST, KASE, ISAVE ) -> (EST, KASE )
```

Estimate the 1-norm of a `real` linear operator `A`, using reverse communication by applying the operator or its transpose/adjoint to a vector. `KASE` is a parameter to control the norm evaluation process as follows. On the initial call, `KASE` should be `0`. On an intermediate return, `KASE` will be `1` or `2`, indicating whether the `real` vector `X` should be overwritten by `A * X`  or `A' * X` at the next call. On the final return, `KASE` will again be `0` and `EST` is an estimate (a lower bound) for the 1-norm of `A`. `V` is a real work vector, `ISGN` is an integer work vector and `ISAVE` is a 3-dimensional integer vector used to save information between the calls. Interface to the LAPACK subroutines DLACN2/SLACN2.
