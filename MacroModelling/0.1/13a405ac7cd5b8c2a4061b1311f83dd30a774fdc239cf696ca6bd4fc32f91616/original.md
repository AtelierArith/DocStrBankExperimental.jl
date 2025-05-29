```julia
get_statistics(
    𝓂,
    parameter_values;
    parameters,
    non_stochastic_steady_state,
    mean,
    standard_deviation,
    variance,
    covariance,
    autocorrelation,
    autocorrelation_periods,
    algorithm,
    quadratic_matrix_equation_algorithm,
    sylvester_algorithm,
    lyapunov_algorithm,
    verbose,
    tol
)

```

Return the first and second moments of endogenous variables using either the linearised solution or the pruned second or pruned third order perturbation solution. By default returns a `Dict` with: non stochastic steady state (NSSS), and standard deviations, but can also return variances, and covariance matrix. Values are returned in the order given for the specific moment. Function to use when differentiating model moments with repect to parameters.

If occasionally binding constraints are present in the model, they are not taken into account here. 

# Arguments

  * `𝓂`: object created by [`@model`](@ref) and [`@parameters`](@ref).
  * `parameter_values` [Type: `Vector`]: Parameter values. If `parameter_names` is not explicitly defined, `parameter_values` are assumed to correspond to the parameters and the order of the parameters declared in the `@parameters` block.

# Keyword Arguments

  * `parameters` [Type: `Vector{Symbol}`]: Corresponding names in the same order as `parameter_values`.
  * `non_stochastic_steady_state` [Default: `Symbol[]`, Type: `Union{Symbol_input,String_input}`]: variables for which to show the NSSS of selected variables. Inputs can be a variable name passed on as either a `Symbol` or `String` (e.g. `:y` or "y"), or `Tuple`, `Matrix` or `Vector` of `String` or `Symbol`. Any variables not part of the model will trigger a warning. `:all_excluding_auxilliary_and_obc` contains all shocks less those related to auxilliary variables and related to occasionally binding constraints (obc). `:all_excluding_obc` contains all shocks less those related to auxilliary variables. `:all` will contain all variables.
  * `mean` [Default: `Symbol[]`, Type: `Union{Symbol_input,String_input}`]: variables for which to show the mean of selected variables (the mean for the linearised solution is the NSSS). Inputs can be a variable name passed on as either a `Symbol` or `String` (e.g. `:y` or "y"), or `Tuple`, `Matrix` or `Vector` of `String` or `Symbol`. Any variables not part of the model will trigger a warning. `:all_excluding_auxilliary_and_obc` contains all shocks less those related to auxilliary variables and related to occasionally binding constraints (obc). `:all_excluding_obc` contains all shocks less those related to auxilliary variables. `:all` will contain all variables.
  * `standard_deviation` [Default: `Symbol[]`, Type: `Union{Symbol_input,String_input}`]: variables for which to show the standard deviation of selected variables. Inputs can be a variable name passed on as either a `Symbol` or `String` (e.g. `:y` or "y"), or `Tuple`, `Matrix` or `Vector` of `String` or `Symbol`. Any variables not part of the model will trigger a warning. `:all_excluding_auxilliary_and_obc` contains all shocks less those related to auxilliary variables and related to occasionally binding constraints (obc). `:all_excluding_obc` contains all shocks less those related to auxilliary variables. `:all` will contain all variables.
  * `variance` [Default: `Symbol[]`, Type: `Union{Symbol_input,String_input}`]: variables for which to show the variance of selected variables. Inputs can be a variable name passed on as either a `Symbol` or `String` (e.g. `:y` or "y"), or `Tuple`, `Matrix` or `Vector` of `String` or `Symbol`. Any variables not part of the model will trigger a warning. `:all_excluding_auxilliary_and_obc` contains all shocks less those related to auxilliary variables and related to occasionally binding constraints (obc). `:all_excluding_obc` contains all shocks less those related to auxilliary variables. `:all` will contain all variables.
  * `covariance` [Default: `Symbol[]`, Type: `Union{Symbol_input,String_input}`]: variables for which to show the covariance of selected variables. Inputs can be a variable name passed on as either a `Symbol` or `String` (e.g. `:y` or "y"), or `Tuple`, `Matrix` or `Vector` of `String` or `Symbol`. Any variables not part of the model will trigger a warning. `:all_excluding_auxilliary_and_obc` contains all shocks less those related to auxilliary variables and related to occasionally binding constraints (obc). `:all_excluding_obc` contains all shocks less those related to auxilliary variables. `:all` will contain all variables.
  * `autocorrelation` [Default: `Symbol[]`, Type: `Union{Symbol_input,String_input}`]: variables for which to show the autocorrelation of selected variables. Inputs can be a variable name passed on as either a `Symbol` or `String` (e.g. `:y` or "y"), or `Tuple`, `Matrix` or `Vector` of `String` or `Symbol`. Any variables not part of the model will trigger a warning. `:all_excluding_auxilliary_and_obc` contains all shocks less those related to auxilliary variables and related to occasionally binding constraints (obc). `:all_excluding_obc` contains all shocks less those related to auxilliary variables. `:all` will contain all variables.
  * `autocorrelation_periods` [Default: `1:5`, Type = `UnitRange{Int}`]: periods for which to return the autocorrelation of selected variables
  * `algorithm` [Default: `:first_order`, Type: `Symbol`]: algorithm to solve for the dynamics of the model. Available algorithms: `:first_order`, `:second_order`, `:pruned_second_order`, `:third_order`, `:pruned_third_order`
  * `quadratic_matrix_equation_algorithm` [Default: `:schur`, Type: `Symbol`]: algorithm to solve quadratic matrix equation (`A * X ^ 2 + B * X + C = 0`). Available algorithms: `:schur`, `:doubling`
  * `lyapunov_algorithm` [Default: `:doubling`, Type: `Symbol`]: algorithm to solve Lyapunov equation (`A * X * A' + C = X`). Available algorithms: `:doubling`, `:bartels_stewart`, `:bicgstab`, `:gmres`
  * `sylvester_algorithm` [Default: function of size of problem, with smaller problems: `:doubling`, and larger problems: `:bicgstab`, Type: `Union{Symbol,Vector{Symbol},Tuple{Symbol,Vararg{Symbol}}}`]: algorithm to solve Sylvester equation (`A * X * B + C = X`). Available algorithms: `:doubling`, `:bartels_stewart`, `:bicgstab`, `:dqgmres`, `:gmres`. Input argument can be up to two elements in a `Vector` or `Tuple`. The first (second) element corresponds to the second (third) order perturbation solutions' Sylvester equation. If only one element is provided it corresponds to the second order perturbation solutions' Sylvester equation.
  * `tol` [Default: `Tolerances()`, Type: `Tolerances`]: define various tolerances for the algorithm used to solve the model. See documentation of [`Tolerances`](@ref) for more details: `?Tolerances`
  * `verbose` [Default: `false`, Type: `Bool`]: print information about results of the different solvers used to solve the model (non stochastic steady state solver, Sylvester equations, Lyapunov equation, and quadratic matrix equation).

# Returns

  * `Dict` with the name of the statistics and the corresponding vectors (NSSS, mean, standard deviation, variance) or matrices (covariance, autocorrelation).

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

get_statistics(RBC, RBC.parameter_values, parameters = RBC.parameters, standard_deviation = RBC.var)
# output
Dict{Symbol, AbstractArray{Float64}} with 1 entry:
  :standard_deviation => [0.0266642, 0.264677, 0.0739325, 0.0102062]
```
