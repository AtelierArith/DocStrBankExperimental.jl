```
gradview(sess::PyObject, pl::PyObject, loss::PyObject, u0; scale::Float64 = 1.0)
```

Visualizes the automatic differentiation and finite difference convergence converge. For correctly implemented differentiable codes, the convergence rate for AD should be 2 and for FD should be 1 (if not evaluated at stationary point).

  * `scale`: you can control the step size for perturbation.
