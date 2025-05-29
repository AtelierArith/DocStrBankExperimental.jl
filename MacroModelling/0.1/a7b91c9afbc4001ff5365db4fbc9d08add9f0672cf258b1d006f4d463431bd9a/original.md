```julia
get_loglikelihood(
    𝓂,
    data,
    parameter_values;
    algorithm,
    filter,
    warmup_iterations,
    presample_periods,
    initial_covariance,
    filter_algorithm,
    tol,
    quadratic_matrix_equation_algorithm,
    lyapunov_algorithm,
    sylvester_algorithm,
    verbose
)

```

Return the loglikelihood of the model given the data and parameters provided. The loglikelihood is either calculated based on the inversion or the Kalman filter (depending on the `filter` keyword argument). In case of a nonlinear solution algorithm the inversion filter will be used. The data must be provided as a `KeyedArray{Float64}` with the names of the variables to be matched in rows and the periods in columns.

This function is differentiable (so far for the Kalman filter only) and can be used in gradient based sampling or optimisation.

If occasionally binding constraints are present in the model, they are not taken into account here. 

# Arguments

  * `𝓂`: object created by [`@model`](@ref) and [`@parameters`](@ref).
  * `data` [Type: `KeyedArray`]: data matrix with variables (`String` or `Symbol`) in rows and time in columns
  * `parameter_values` [Type: `Vector`]: Parameter values.

# Keyword Arguments

  * `algorithm` [Default: `:first_order`, Type: `Symbol`]: algorithm to solve for the dynamics of the model. Available algorithms: `:first_order`, `:second_order`, `:pruned_second_order`, `:third_order`, `:pruned_third_order`
  * `filter` [Default: `:kalman`, Type: `Symbol`]: filter used to compute the variables, and shocks given the data, model, and parameters. The Kalman filter only works for linear problems, whereas the inversion filter (`:inversion`) works for linear and nonlinear models. If a nonlinear solution algorithm is selected, the inversion filter is used.
  * `presample_periods` [Default: `0`, Type: `Int`]: periods at the beginning of the data for which the loglikelihood is discarded.
  * `initial_covariance` [Default: `:theoretical`, Type: `Symbol`]: defines the method to initialise the Kalman filters covariance matrix. It can be initialised with the theoretical long run values (option `:theoretical`) or large values (10.0) along the diagonal (option `:diagonal`).
  * `quadratic_matrix_equation_algorithm` [Default: `:schur`, Type: `Symbol`]: algorithm to solve quadratic matrix equation (`A * X ^ 2 + B * X + C = 0`). Available algorithms: `:schur`, `:doubling`
  * `sylvester_algorithm` [Default: function of size of problem, with smaller problems: `:doubling`, and larger problems: `:bicgstab`, Type: `Union{Symbol,Vector{Symbol},Tuple{Symbol,Vararg{Symbol}}}`]: algorithm to solve Sylvester equation (`A * X * B + C = X`). Available algorithms: `:doubling`, `:bartels_stewart`, `:bicgstab`, `:dqgmres`, `:gmres`. Input argument can be up to two elements in a `Vector` or `Tuple`. The first (second) element corresponds to the second (third) order perturbation solutions' Sylvester equation. If only one element is provided it corresponds to the second order perturbation solutions' Sylvester equation.
  * `lyapunov_algorithm` [Default: `:doubling`, Type: `Symbol`]: algorithm to solve Lyapunov equation (`A * X * A' + C = X`). Available algorithms: `:doubling`, `:bartels_stewart`, `:bicgstab`, `:gmres`
  * `tol` [Default: `Tolerances()`, Type: `Tolerances`]: define various tolerances for the algorithm used to solve the model. See documentation of [`Tolerances`](@ref) for more details: `?Tolerances`
  * `verbose` [Default: `false`, Type: `Bool`]: print information about results of the different solvers used to solve the model (non stochastic steady state solver, Sylvester equations, Lyapunov equation, and quadratic matrix equation).

# Returns

  * `<:AbstractFloat` loglikelihood

# Examples

```jldoctest
using MacroModelling

@model RBC begin
    1  /  c[0] = (β  /  c[1]) * (α * exp(z[1]) * k[0]^(α - 1) + (1 - δ))
    c[0] + k[0] = (1 - δ) * k[-1] + q[0]
    q[0] = exp(z[0]) * k[-1]^α
    z[0] = ρ * z[-1] + std_z * eps_z[x]
end

@parameters RBC begin
    std_z = 0.01
    ρ = 0.2
    δ = 0.02
    α = 0.5
    β = 0.95
end

simulated_data = simulate(RBC)

get_loglikelihood(RBC, simulated_data([:k], :, :simulate), RBC.parameter_values)
# output
58.24780188977981
```
