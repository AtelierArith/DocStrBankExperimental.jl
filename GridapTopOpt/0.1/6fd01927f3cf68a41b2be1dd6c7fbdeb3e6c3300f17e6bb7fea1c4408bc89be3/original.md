```
struct PDEConstrainedFunctionals{N,A}
```

An object that computes the objective, constraints, and their derivatives.

# Implementation

This implementation computes derivatives of a integral quantity

$F(u(\varphi),\varphi,\mathrm{d}\Omega_1,\mathrm{d}\Omega_2,...) = \Sigma_{i}\int_{\Omega_i} f_i(\varphi)~\mathrm{d}\Omega$

with respect to an auxiliary parameter $\varphi$ where $u$ is the solution to a PDE and implicitly depends on $\varphi$. This requires two pieces of information:

1. Computation of $\frac{\partial F}{\partial u}$ and $\frac{\partial F}{\partial \varphi}$ (handled by [`StateParamIntegrandWithMeasure`](@ref)).
2. Computation of $\frac{\partial F}{\partial u} \frac{\partial u}{\partial \varphi}$ at $\varphi$ and $u$ using the adjoint method (handled by [`AbstractFEStateMap`](@ref)). I.e., let

    $\frac{\partial F}{\partial u} \frac{\partial u}{\partial \varphi} = -\lambda^\intercal \frac{\partial \mathcal{R}}{\partial \varphi}$

    where $\mathcal{R}$ is the residual and solve the (linear) adjoint problem:

    $\frac{\partial \mathcal{R}}{\partial u}^\intercal\lambda = \frac{\partial F}{\partial u}^\intercal.$

The gradient is then $\frac{\partial F}{\partial \varphi} = \frac{\partial F}{\partial \varphi} - \frac{\partial F}{\partial u}\frac{\partial u}{\partial \varphi}$.

# Parameters

  * `J`: A `StateParamIntegrandWithMeasure` corresponding to the objective.
  * `C`: A vector of `StateParamIntegrandWithMeasure` corresponding to the constraints.
  * `dJ`: The DoFs for the objective sensitivity.
  * `dC`: The DoFs for each constraint sensitivity.
  * `analytic_dJ`: a `Function` for computing the analytic objective sensitivity.
  * `analytic_dC`: A vector of `Function` for computing the analytic objective sensitivities.
  * `state_map::A`: The state map for the problem.

# Note

  * If `analytic_dJ = nothing` automatic differentiation will be used.
  * If `analytic_dC[i] = nothing` automatic differentiation will be used for `C[i]`.
