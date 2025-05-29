```
provide_rule(func, x, p=(); mode="ffd", jacobian=nothing, jvp=nothing, vjp=nothing)
```

Provide partials rather than rely on AD.  For cases where AD is not available or to provide your own rule, or to use mixed mode, etc.

# Arguments

  * `func::function`, `x::vector{float}`, `p::tuple`:  function of form: y = func(x, p), where x are variables and p are fixed parameters.
  * `mode::string`:

      * "ffd": forward finite difference
      * "cfd": central finite difference
      * "cs": complex step
      * "jacobian": provide your own jacobian (see jacobian function)
      * "vp": provide jacobian vector product and vector jacobian product (see jvp and vjp)
  * `jacobian::function`: only used if mode="jacobian". J = jacobian(x, p) provide J*ij = dy*i / dx_j
  * `jvp::function`: only used if mode="vp" and in forward mode. ydot = jvp(x, p, v) provide Jacobian vector product J*v
  * `vjp::function`: only used if mode="vp" and in revese mode. xbar = vjp(x, p, v) provide vector Jacobian product v'*J
