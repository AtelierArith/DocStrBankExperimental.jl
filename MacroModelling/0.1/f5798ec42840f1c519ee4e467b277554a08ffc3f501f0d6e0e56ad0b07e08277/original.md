```julia
get_conditional_variance_decomposition(
    𝓂;
    periods,
    parameters,
    verbose,
    tol,
    quadratic_matrix_equation_algorithm,
    lyapunov_algorithm
)

```

Return the conditional variance decomposition of endogenous variables with regards to the shocks using the linearised solution. 

If occasionally binding constraints are present in the model, they are not taken into account here. 

# Arguments

  * `𝓂`: object created by [`@model`](@ref) and [`@parameters`](@ref).

# Keyword Arguments

  * `periods` [Default: `[1:20...,Inf]`, Type: `Union{Vector{Int},Vector{Float64},UnitRange{Int64}}`]: vector of periods for which to calculate the conditional variance decomposition. If the vector conatins `Inf`, also the unconditional variance decomposition is calculated (same output as [`get_variance_decomposition`](@ref)).
  * `parameters` [Default: `nothing`]: If `nothing` is provided, the solution is calculated for the parameters defined previously. Acceptable inputs are a `Vector` of parameter values, a `Vector` or `Tuple` of `Pair`s of the parameter `Symbol` or `String` and value. If the new parameter values differ from the previously defined the solution will be recalculated.
  * `quadratic_matrix_equation_algorithm` [Default: `:schur`, Type: `Symbol`]: algorithm to solve quadratic matrix equation (`A * X ^ 2 + B * X + C = 0`). Available algorithms: `:schur`, `:doubling`
  * `lyapunov_algorithm` [Default: `:doubling`, Type: `Symbol`]: algorithm to solve Lyapunov equation (`A * X * A' + C = X`). Available algorithms: `:doubling`, `:bartels_stewart`, `:bicgstab`, `:gmres`
  * `tol` [Default: `Tolerances()`, Type: `Tolerances`]: define various tolerances for the algorithm used to solve the model. See documentation of [`Tolerances`](@ref) for more details: `?Tolerances`
  * `verbose` [Default: `false`, Type: `Bool`]: print information about results of the different solvers used to solve the model (non stochastic steady state solver, Sylvester equations, Lyapunov equation, and quadratic matrix equation).

# Returns

  * `KeyedArray` with variables in rows, shocks in columns, and periods as the third dimension.

# Examples

```jldoctest part1
using MacroModelling

@model RBC_CME begin
    y[0]=A[0]*k[-1]^alpha
    1/c[0]=beta*1/c[1]*(alpha*A[1]*k[0]^(alpha-1)+(1-delta))
    1/c[0]=beta*1/c[1]*(R[0]/Pi[+1])
    R[0] * beta =(Pi[0]/Pibar)^phi_pi
    A[0]*k[-1]^alpha=c[0]+k[0]-(1-delta*z_delta[0])*k[-1]
    z_delta[0] = 1 - rho_z_delta + rho_z_delta * z_delta[-1] + std_z_delta * delta_eps[x]
    A[0] = 1 - rhoz + rhoz * A[-1]  + std_eps * eps_z[x]
end

@parameters RBC_CME begin
    alpha = .157
    beta = .999
    delta = .0226
    Pibar = 1.0008
    phi_pi = 1.5
    rhoz = .9
    std_eps = .0068
    rho_z_delta = .9
    std_z_delta = .005
end

get_conditional_variance_decomposition(RBC_CME)
# output
3-dimensional KeyedArray(NamedDimsArray(...)) with keys:
↓   Variables ∈ 7-element Vector{Symbol}
→   Shocks ∈ 2-element Vector{Symbol}
◪   Periods ∈ 21-element Vector{Float64}
And data, 7×2×21 Array{Float64, 3}:
[showing 3 of 21 slices]
[:, :, 1] ~ (:, :, 1.0):
              (:delta_eps)  (:eps_z)
  (:A)         0.0           1.0
  (:Pi)        0.00158668    0.998413
  (:R)         0.00158668    0.998413
  (:c)         0.0277348     0.972265
  (:k)         0.00869568    0.991304
  (:y)         0.0           1.0
  (:z_delta)   1.0           0.0

[:, :, 11] ~ (:, :, 11.0):
              (:delta_eps)  (:eps_z)
  (:A)         5.88653e-32   1.0
  (:Pi)        0.0245641     0.975436
  (:R)         0.0245641     0.975436
  (:c)         0.0175249     0.982475
  (:k)         0.00869568    0.991304
  (:y)         7.63511e-5    0.999924
  (:z_delta)   1.0           0.0

[:, :, 21] ~ (:, :, Inf):
              (:delta_eps)  (:eps_z)
  (:A)         9.6461e-31    1.0
  (:Pi)        0.0156771     0.984323
  (:R)         0.0156771     0.984323
  (:c)         0.0134672     0.986533
  (:k)         0.00869568    0.991304
  (:y)         0.000313462   0.999687
  (:z_delta)   1.0           0.0
```
