```julia
get_autocorrelation(
    𝓂;
    autocorrelation_periods,
    parameters,
    algorithm,
    quadratic_matrix_equation_algorithm,
    sylvester_algorithm,
    lyapunov_algorithm,
    verbose,
    tol
)

```

Return the autocorrelations of endogenous variables using the first, pruned second, or pruned third order perturbation solution. 

If occasionally binding constraints are present in the model, they are not taken into account here. 

# Arguments

  * `𝓂`: object created by [`@model`](@ref) and [`@parameters`](@ref).

# Keyword Arguments

  * `autocorrelation_periods` [Default: `1:5`, Type: `UnitRange{Int}`]: periods for which to return the autocorrelation
  * `parameters` [Default: `nothing`]: If `nothing` is provided, the solution is calculated for the parameters defined previously. Acceptable inputs are a `Vector` of parameter values, a `Vector` or `Tuple` of `Pair`s of the parameter `Symbol` or `String` and value. If the new parameter values differ from the previously defined the solution will be recalculated.
  * `algorithm` [Default: `:first_order`, Type: `Symbol`]: algorithm to solve for the dynamics of the model. Available algorithms: `:first_order`, `:second_order`, `:pruned_second_order`, `:third_order`, `:pruned_third_order`
  * `quadratic_matrix_equation_algorithm` [Default: `:schur`, Type: `Symbol`]: algorithm to solve quadratic matrix equation (`A * X ^ 2 + B * X + C = 0`). Available algorithms: `:schur`, `:doubling`
  * `lyapunov_algorithm` [Default: `:doubling`, Type: `Symbol`]: algorithm to solve Lyapunov equation (`A * X * A' + C = X`). Available algorithms: `:doubling`, `:bartels_stewart`, `:bicgstab`, `:gmres`
  * `sylvester_algorithm` [Default: function of size of problem, with smaller problems: `:doubling`, and larger problems: `:bicgstab`, Type: `Union{Symbol,Vector{Symbol},Tuple{Symbol,Vararg{Symbol}}}`]: algorithm to solve Sylvester equation (`A * X * B + C = X`). Available algorithms: `:doubling`, `:bartels_stewart`, `:bicgstab`, `:dqgmres`, `:gmres`. Input argument can be up to two elements in a `Vector` or `Tuple`. The first (second) element corresponds to the second (third) order perturbation solutions' Sylvester equation. If only one element is provided it corresponds to the second order perturbation solutions' Sylvester equation.
  * `tol` [Default: `Tolerances()`, Type: `Tolerances`]: define various tolerances for the algorithm used to solve the model. See documentation of [`Tolerances`](@ref) for more details: `?Tolerances`
  * `verbose` [Default: `false`, Type: `Bool`]: print information about results of the different solvers used to solve the model (non stochastic steady state solver, Sylvester equations, Lyapunov equation, and quadratic matrix equation).

# Returns

  * `KeyedArray` with variables in rows and autocorrelation periods in columns.

# Examples

```jldoctest part1
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

get_autocorrelation(RBC)
# output
2-dimensional KeyedArray(NamedDimsArray(...)) with keys:
↓   Variables ∈ 4-element Vector{Symbol}
→   Autocorrelation_periods ∈ 5-element UnitRange{Int64}
And data, 4×5 Matrix{Float64}:
        (1)         (2)         (3)         (4)         (5)
  (:c)    0.966974    0.927263    0.887643    0.849409    0.812761
  (:k)    0.971015    0.931937    0.892277    0.853876    0.817041
  (:q)    0.32237     0.181562    0.148347    0.136867    0.129944
  (:z)    0.2         0.04        0.008       0.0016      0.00032
```
