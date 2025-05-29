```
NLSMeta
```

Base type for metadata related to a nonlinear least-squares model.

---

```
NLSMeta(nequ, nvar; kwargs...)
```

Create a `NLSMeta` with `nequ` equations and `nvar` variables. The following keyword arguments are accepted:

  * `x0`: initial guess
  * `nnzj`: number of elements needed to store the nonzeros of the Jacobian of the residual
  * `nnzh`: number of elements needed to store the nonzeros of the sum of Hessians of the residuals
  * `lin`: indices of linear residuals

`NLSMeta` also contains the following attributes, which are computed from the variables above:

  * `nequ`: size of the residual
  * `nvar`: number of variables
  * `nln`: indices of nonlinear residuals
  * `nnln`: number of nonlinear general residuals
  * `nlin`: number of linear residuals
