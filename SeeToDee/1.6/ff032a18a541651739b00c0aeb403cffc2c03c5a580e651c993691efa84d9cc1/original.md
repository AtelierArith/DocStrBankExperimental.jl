```
SimpleColloc(dyn, Ts, nx, na, nu; n = 5, abstol = 1.0e-8, solver=SimpleNewtonRaphson(), residual=false)
SimpleColloc(dyn, Ts, x_inds, a_inds, nu; n = 5, abstol = 1.0e-8, solver=SimpleNewtonRaphson(), residual=false)
```

A simple direct-collocation integrator that can be stepped manually, similar to the function returned by [`SeeToDee.Rk4`](@ref).

This integrator supports differential-algebraic equations (DAE), the dynamics is expected to be on either of the forms 

  * `nx,na` provided: `(xz,u,p,t)->[ẋ; res]` where `xz` is a vector `[x; z]` contaning the differential state `x` and the algebraic variables `z` in this order. `res` is the algebraic residuals, and `u` is the control input. The algebraic residuals are thus assumed to be the last `na` elements of of the arrays returned by the dynamics (the convention used by ModelingToolkit).
  * `x_inds, a_inds` provided: `(xz,u,p,t)->xzd` where `xzd[x_inds] = ẋ` and `xzd[a_inds] = res`.

The returned function has the signature `f_discrete : (x,u,p,t)->x(t+Tₛ)`. 

This integrator also supports a fully implicit form of the dynamics

$$
0 = F(ẋ, x, u, p, t)
$$

When using this interface, the dynamics is called using an additional input `ẋ` as the first argument, and the return value is expected to be the residual of the entire state descriptor. To use the implicit form, pass `residual = true`.

A Gauss-Radau collocation method is used to discretize the dynamics. The resulting nonlinear problem is solved using (by default) a Newton-Raphson method. This method handles stiff dynamics.

# Arguments:

  * `dyn`: Dynamics function (continuous time)
  * `Ts`: Sample time
  * `nx`: Number of differential state variables
  * `na`: Number of algebraic variables
  * `x_inds, a_inds`: If indices are provided instead of `nx` and `na`, the mass matrix is assumed to be diagonal, with ones located at `x_inds` and zeros at `a_inds`. For maximum efficiency, provide these indices as unit ranges or static arrays.
  * `nu`: Number of inputs
  * `n`: Number of collocation points. `n=2` corresponds to trapezoidal integration.
  * `abstol`: Tolerance for the root finding algorithm
  * `residual`: If `true` the dynamics function is assumed to return the residual of the entire state descriptor and have the signature `(ẋ, x, u, p, t) -> res`. This is sometimes called "fully implicit form".
  * `solver`: Any compatible SciML Nonlinear solver to use for the root finding problem

# Extended help

  * Super-sampling is not supported by this integrator, but you can trivially wrap it in a function that does super-sampling by stepping `supersample` times in a loop with the same input and sample time `Ts / supersample`.
