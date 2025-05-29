```
`shamanskii_stop(h :: Any, h_at_t :: OneDAtX; γ :: Float64 = 1.0e-09, kwargs...)`
```

Check if a step size is admissible according to the "Shamanskii" criteria.

This criteria was proposed in:

> Lampariello, F., & Sciandrone, M. (2001). Global convergence technique for the Newton method with periodic Hessian evaluation. Journal of optimization theory and applications, 111(2), 341-358.


Note: 

  * `h.d` accessible (specific `LineModel`).
  * `fx`, `f₀` are required in the `OneDAtX`.

See also `armijo`, `wolfe`, `armijo_wolfe`, `goldstein`
