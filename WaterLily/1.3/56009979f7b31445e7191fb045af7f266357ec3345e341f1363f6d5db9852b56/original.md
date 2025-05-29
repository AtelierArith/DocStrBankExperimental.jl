```
solver!(A::Poisson;log,tol,itmx)
```

Approximate iterative solver for the Poisson matrix equation `Ax=b`.

  * `A`: Poisson matrix with working arrays.
  * `A.x`: Solution vector. Can start with an initial guess.
  * `A.z`: Right-Hand-Side vector. Will be overwritten!
  * `A.n[end]`: stores the number of iterations performed.
  * `log`: If `true`, this function returns a vector holding the `L₂`-norm of the residual at each iteration.
  * `tol`: Convergence tolerance on the `L₂`-norm residual.
  * `itmx`: Maximum number of iterations.
