```
struct NonlinearFEStateMap{A,B,C,D,E,F} <: AbstractFEStateMap
```

A structure to enable the forward problem and pullback for nonlinear finite element operators.

# Parameters

  * `res::A`: an `IntegrandWithMeasure` defining the residual of the problem.
  * `jac::B`: a `Function` defining Jacobian of the residual.
  * `spaces::C`: `Tuple` of finite element spaces.
  * `plb_caches::D`: A cache for the pullback operator.
  * `fwd_caches::E`: A cache for the forward problem.
  * `adj_caches::F`: A cache for the adjoint problem.
