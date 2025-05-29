```
PEtabODEProblem(model::PEtabModel; kwargs...)
```

From `model` create a `PEtabODEProblem` for parameter estimation/inference.

If no options (`kwargs`) are provided, default settings are used for the `ODESolver`, gradient method, and Hessian method. For more information on the default options, see the documentation.

See also [`ODESolver`](@ref), [`SteadyStateSolver`](@ref), and [`PEtabModel`](@ref).

# Keyword Arguments

  * `odesolver::ODESolver`: ODE solver options for computing the likelihood (objective   function).
  * `odesolver_gradient::ODESolver`: ODE solver options for computing the gradient. Defaults   to `odesolver` if not provided.
  * `ss_solver::SteadyStateSolver`: Steady-state solver options for computing the likelihood.   Only applicable for models with steady-state simulations.
  * `ss_solver_gradient::SteadyStateSolver`: Steady-state solver options for computing the   gradient. Defaults to `ss_solver` if not provided.
  * `gradient_method::Symbol`: Method for computing the gradient. Available options and   defaults are listed in the documentation.
  * `hessian_method::Symbol`: Method for computing the Hessian. As with the gradient,   available options and defaults can be found in the documentation.
  * `FIM_method=nothing`: Method for computing the empirical Fisher Information Matrix (FIM).   Accepts the same options as `hessian_method`.
  * `sparse_jacobian=false`: Whether to use a sparse Jacobian when solving the ODE model.   This can greatly improve performance for large models.
  * `sensealg`: Sensitivity algorithm for gradient computations. Available and default   options depend on `gradient_method`. See the documentation for details.
  * `chunksize=nothing`: Chunk size for ForwardDiff.jl when using forward-mode automatic   differentiation for gradients and Hessians. If not provided, a default value is used.   Tuning `chunksize` can improve performance but is non-trivial.
  * `split_over_conditions::Bool=false`: Whether to split ForwardDiff.jl calls across   simulation conditions when computing the gradient and/or Hessian. This improves   performance for models with many condition-specific parameters, otherwise it increases   runtime.
  * `reuse_sensitivities::Bool=false`: Whether to reuse forward sensitivities from the   gradient computation for the Gauss-Newton Hessian approximation. Only applies when   `hessian_method=:GaussNewton` and `gradient_method=:ForwardEquations`. This can greatly   improve  performance when the optimization algorithm computes both the gradient and   Hessian simultaneously.
  * `verbose::Bool = false`: Whether to print progress while building the `PEtabODEProblem`.

## Returns

A `PEtabODEProblem`, where the key fields are:

  * `nllh`: Compute the negative log-likelihood function for an input vector `x`;   `nllh(x)`. For this function and the ones below listed below, the input `x` can be   either a `Vector` or a `ComponentArray`.
  * `grad!`: Compute the in-place gradient of the nllh; `grad!(g, x)`.
  * `grad`: Compute the out-of-place gradient of the nllh; `g = grad(x)`.
  * `hess!`: Compute the in-place Hessian of the nllh; `hess!(H, x)`.
  * `hess`: Compute the out-of-place Hessian of the nllh; `H = hess(x)`.
  * `FIM`: Compute the out-of-place empirical Fisher Information Matrix (FIM) of the nllh;   `F = FIM(x)`.
  * `chi2`: Compute the chi-squared test statistic for the nllh (see mathematical definition   below); `χ² = chi2(x)`.
  * `residuals`: Computes the residuals between the measurement data and model output (see   the mathematical definition below); `r = residuals(x)`.
  * `simulated_values`: Computes the corresponding model values for each measurement in the   measurements table, in the same order as the measurements appear.
  * `lower_bounds`: Lower parameter bounds for parameter estimation, as specified when   creating the `model`.
  * `upper_bounds`: Upper parameter bounds for parameter estimation, as specified when   creating the `model`.

## Description

Following the [PEtab standard](https://petab.readthedocs.io/en/latest/), the objective function to be used for parameter estimation created by the `PEtabODEProblem` is a likelihood function, or, if priors are provided, a posterior function. The characteristics of the objective is defined in the `PEtabModel`. In practice, for numerical stability, a `PEtabODEProblem` works with the negative log-likelihood:

$$
-\ell(\mathbf{x}) =  - \sum_{i = 1}^N \ell_i(\mathbf{x}),
$$

where $\ell_i$ is the likelihood for each measurement $i$. In addition, to accommodate numerical optimization packages, the `PEtabODEProblem` provides efficient functions for computing the gradient $-\nabla \ell(\mathbf{x})$ and the second derivative Hessian matrix $-\nabla^2 \ell(\mathbf{x})$, using the specified or default `gradient_method` and `hessian_method`.

In addition to $-\ell$ and its derivatives, the `PEtabODEProblem` provides functions for diagnostics and model selection. The χ² (chi-squared) value can be used for model selection [1], and it is computed as the sum of the χ² values for each measurement. For a measurement `y`, an observable `h = obs_formula`, and a standard deviation `σ = noise_formula`, the χ² is computed as:

$$
\chi^2 = \frac{(y - h)^2}{\sigma^2}
$$

The residuals $r$ can be used to assess the measurement error model and are computed as:

$$
r = \frac{(y - h)}{\sigma}
$$

Lastly, the empirical Fisher Information Matrix (FIM) can be used for identifiability analysis [2]. It should ideally be computed with an exact Hessian method. The inverse of the FIM provides a lower bound on the covariance matrix. While the FIM can be useful, the profile-likelihood approach generally yields better results for identifiability analysis [2].

1. Cedersund et al, The FEBS journal, pp 903-922 (2009).
2. Raue et al, Bioinformatics, pp 1923-1929 (2009).
