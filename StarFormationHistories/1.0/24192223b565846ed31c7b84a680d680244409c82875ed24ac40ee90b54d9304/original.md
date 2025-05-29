```
result = fit_templates(models::AbstractVector{T},
                       data::AbstractMatrix{<:Number};
                       x0::AbstractVector{<:Number} = ones(S,length(models)),
                       kws...) where {S <: Number, T <: AbstractMatrix{S}}
```

Finds both maximum likelihood estimate (MLE) and maximum a posteriori estimate (MAP) for the coefficients `coeffs` such that the composite Hess diagram model is `sum(models .* coeffs)` using the provided templates `models` and the observed Hess diagram `data`. Utilizes the Poisson likelihood ratio (equations 7–10 in [Dolphin 2002](https://ui.adsabs.harvard.edu/abs/2002MNRAS.332...91D)) for the likelihood of the data given the model. See the examples in the documentation for comparisons of the results of this method and [`hmc_sample`](@ref) which samples the posterior via Hamiltonian Monte Carlo. 

# Arguments

  * `models::AbstractVector{AbstractMatrix{<:Number}}`: the list of template Hess diagrams for the simple stellar populations (SSPs) being considered; all must have the same size.
  * `data::AbstractMatrix{<:Number}`: the observed Hess diagram; must match the size of the templates contained in `models`.

# Keyword Arguments

  * `x0`: The vector of initial guesses for the stellar mass coefficients. You should basically always be calculating and passing this keyword argument; we provide [`StarFormationHistories.construct_x0`](@ref) to prepare `x0` assuming constant star formation rate, which is typically a good initial guess.

Other `kws...` are passed to `Optim.options` to set things like convergence criteria for the optimization. 

# Returns

`result` is a `NamedTuple` containing two [`StarFormationHistories.LogTransformFTResult`](@ref). The two components of `result` are `result.map` or `result[1]`, which contains the results of the MAP optimization, and `result.mle` or `result[2]`, which contains the results of the MLE optimization. The documentation for [`StarFormationHistories.LogTransformFTResult`](@ref) contains more information about these types, but briefly they contain the following fields, accessible as, e.g., `result.map.μ`, `result.map.σ`, etc.:

  * `μ::Vector{<:Number}` are the optimized `coeffs` at the maximum.
  * `σ::Vector{<:Number}` are the standard errors on the coeffs `μ` calculated from an estimate of the inverse Hessian matrix evaluated at `μ`. The inverse of the Hessian matrix at the maximum of the likelihood (or posterior) is a estimator for the variance-covariance matrix of the parameters, but is only accurate when the second-order expansion given by the Hessian at the maximum is a good approximation to the function being optimized (i.e., when the optimized function is approximately quadratic around the maximum; see [Dovi et al. 1991](https://doi.org/10.1016/0893-9659(91)90129-J) for more information). We find this is often the case for the MAP estimate, but the errors found for coefficients that are ≈0 in the MLE are typically unrealistically small. For coefficients significantly greater than 0, the `σ` values from the MAP and MLE are typically consistent to 5–10%.
  * `invH::Matrix{<:Number}` is the estimate of the inverse Hessian matrix at `μ` that was used to derive `σ`. The optimization is done under a logarithmic transform, such that `θ[j] = log(coeffs[j])` are the actual parameters optimized, so the entries in the Hessian are actually

$$
H^{(j,k)} ( \boldsymbol{\hat \theta} ) = \left. \frac{\partial^2 \, J(\boldsymbol{\theta})}{\partial \theta_j \, \partial \theta_k} \right\vert_{\boldsymbol{\theta}=\boldsymbol{\hat \theta}}
$$

  * `result` is the full object returned by the optimization from `Optim.jl`; this is of type `Optim.MultivariateOptimizationResults`. Remember that the optimization is done with parameters `θ[j] = log(coeffs[j])` when dealing with this raw output. This means that, for example, we calculate `result.map.μ` as `exp.(Optim.minimizer(result.map.result))`.

The special property of the [`StarFormationHistories.LogTransformFTResult`](@ref) type is that you can draw a set of `N::Integer` random parameter samples from the result using the inverse Hessian approximation discussed above by doing `rand(result.map, N)`. This type implements the random sampling API of `Distributions.jl` so the other standard sampling methods should work as well. In our tests these samples compare very favorably against those from [`hmc_sample`](@ref), which samples the posterior via Hamiltonian Monte Carlo and is therefore more robust but much more expensive. We compare these methods in the examples.

# Notes

  * This method uses the `BFGS` method from `Optim.jl` internally because it builds and tracks the inverse Hessian matrix approximation which can be used to estimate parameter uncertainties. BFGS is much more memory-intensive than LBFGS (as used for [`StarFormationHistories.fit_templates_lbfgsb`](@ref)) for large numbers of parameters (equivalently, many `models`), so you should consider LBFGS to solve for the MLE along with [`hmc_sample`](@ref) to sample the posterior if you are using a large grid of models (greater than a few hundred).
  * The BFGS implementation we use from Optim.jl uses BLAS operations during its iteration. The OpenBLAS that Julia ships with will often default to running on multiple threads even if Julia itself is started with only a single thread. You can check the current number of BLAS threads with `import LinearAlgebra: BLAS; BLAS.get_num_threads()`. For the problem sizes typical of this function we actually see performance regression with larger numbers of BLAS threads. For this reason you may wish to use BLAS in single-threaded mode; you can set this as `import LinearAlgebra: BLAS; BLAS.set_num_threads(1)`.
