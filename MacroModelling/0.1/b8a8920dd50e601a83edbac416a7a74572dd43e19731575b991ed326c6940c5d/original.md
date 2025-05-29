```julia
get_solution(
    𝓂,
    parameters;
    algorithm,
    verbose,
    tol,
    quadratic_matrix_equation_algorithm,
    sylvester_algorithm
)

```

Return the components of the solution of the model: non-stochastic steady state (NSSS), and solution martrices corresponding to the order of the solution. Note that all returned objects have the variables in rows and the solution matrices have as columns the state variables followed by the perturbation/volatility parameter for higher order solution matrices and lastly the exogenous shocks. Higher order perturbation matrices are sparse and have the Kronecker product of the forementioned elements as columns. The last element, a Boolean indicates whether the solution is numerically accurate. Function to use when differentiating IRFs with repect to parameters.

# Arguments

  * `𝓂`: object created by [`@model`](@ref) and [`@parameters`](@ref).
  * `parameters` [Default: `nothing`]: If `nothing` is provided, the solution is calculated for the parameters defined previously. Acceptable inputs are a `Vector` of parameter values, a `Vector` or `Tuple` of `Pair`s of the parameter `Symbol` or `String` and value. If the new parameter values differ from the previously defined the solution will be recalculated.

# Keyword Arguments

  * `algorithm` [Default: `:first_order`, Type: `Symbol`]: algorithm to solve for the dynamics of the model. Available algorithms: `:first_order`, `:second_order`, `:pruned_second_order`, `:third_order`, `:pruned_third_order`
  * `quadratic_matrix_equation_algorithm` [Default: `:schur`, Type: `Symbol`]: algorithm to solve quadratic matrix equation (`A * X ^ 2 + B * X + C = 0`). Available algorithms: `:schur`, `:doubling`
  * `sylvester_algorithm` [Default: function of size of problem, with smaller problems: `:doubling`, and larger problems: `:bicgstab`, Type: `Union{Symbol,Vector{Symbol},Tuple{Symbol,Vararg{Symbol}}}`]: algorithm to solve Sylvester equation (`A * X * B + C = X`). Available algorithms: `:doubling`, `:bartels_stewart`, `:bicgstab`, `:dqgmres`, `:gmres`. Input argument can be up to two elements in a `Vector` or `Tuple`. The first (second) element corresponds to the second (third) order perturbation solutions' Sylvester equation. If only one element is provided it corresponds to the second order perturbation solutions' Sylvester equation.
  * `tol` [Default: `Tolerances()`, Type: `Tolerances`]: define various tolerances for the algorithm used to solve the model. See documentation of [`Tolerances`](@ref) for more details: `?Tolerances`
  * `verbose` [Default: `false`, Type: `Bool`]: print information about results of the different solvers used to solve the model (non stochastic steady state solver, Sylvester equations, Lyapunov equation, and quadratic matrix equation).

# Returns

  * `Tuple` consisting of a `Vector` containing the NSSS, followed by a `Matrix` containing the first order solution matrix. In case of higher order solutions, `SparseMatrixCSC` represent the higher order solution matrices. The last element is a `Bool` indicating the correctness of the solution provided.

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

get_solution(RBC, RBC.parameter_values)
# output
([5.936252888048724, 47.39025414828808, 6.884057971014486, 0.0], 
 [0.09579643002421227 0.1349373930517757 0.006746869652588215; 
  0.9568351489231555 1.241874201151121 0.06209371005755664; 
  0.07263157894736819 1.376811594202897 0.06884057971014486; 
  0.0 0.19999999999999998 0.01], true)
```
