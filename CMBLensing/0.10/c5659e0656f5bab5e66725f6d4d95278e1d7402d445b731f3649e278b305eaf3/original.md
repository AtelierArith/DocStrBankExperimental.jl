```
LenseFlow(ϕ, [n=7])
```

`LenseFlow` is the ODE-based lensing algorithm from [Millea, Anderes, & Wandelt, 2019](https://arxiv.org/abs/1708.06753). The number of steps in the ODE solver is controlled by `n`. The action of the operator, as well as its adjoint, inverse, inverse-adjoint, and gradient of any of these w.r.t. `ϕ` can all be computed. The log-determinant of the operation is zero independent of `ϕ`, in the limit of `n` high enough.
