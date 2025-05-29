x,flag,err,iter,resvec = minres(A,b,;x=[],maxIter=20,tol=1e-10,out=1)

Minimal Residual Method (MINRES) for solving

```
A x = b,
```

where A is symmetric and possibly indefinite.

Implementation follows page 26 of

Choi, S.-C. T. (2006).   Iterative Methods for Singular Linear Equations and Least-squares Problems.   Phd thesis, Stanford University.

See also:

Paige, C. C., & Saunders, M. A. (1975).   Solution of sparse indefinite systems of linear equations.   SIAM Journal on Numerical Analysis.

Required input:

A       - function that performs matrix-vector product, e.g., x -> A*x    b       - right hand side vector

Optional input:

x        - starting guess (optional)    maxIter  - maximum number of iterations    btol     - error tolerance for Lanczos step    rtol     - error tolerance for estimated relative residual    gtol     - error tolerance for estimated gradient norm    condlim  - limit on condition number esitmate of A    out      - flag for output (-1: no output, 0: only errors, 1: final status, 2: residual norm at each iteration)

Output:

x       - approximate solution   flag    - exit flag (0: converged, -1: maxIter, -2: Lanczos, -3: condition)   relres  - estimated relative residual at final iteration   nrmG    - estimated gradient norm at final iteration   nrmA    - estimated Frobenius norm of A   conA    - condition number estimate   phi     - relres for each iteration
