Adds parameter values and calibration equations to the previously defined model. Allows to provide an initial guess for the non-stochastic steady state (NSSS).

# Arguments

  * `𝓂`: name of the object previously created containing the model information.
  * `ex`: parameter, parameters values, and calibration equations

Parameters can be defined in either of the following ways:

  * plain number: `δ = 0.02`
  * expression containing numbers: `δ = 1/50`
  * expression containing other parameters: `δ = 2 * std_z` in this case it is irrelevant if `std_z` is defined before or after. The definitons including other parameters are treated as a system of equaitons and solved accordingly.
  * expressions containing a target parameter and an equations with endogenous variables in the non-stochastic steady state, and other parameters, or numbers: `k[ss] / (4 * q[ss]) = 1.5 | δ` or `α | 4 * q[ss] = δ * k[ss]` in this case the target parameter will be solved simultaneaously with the non-stochastic steady state using the equation defined with it.

# Optional arguments to be placed between `𝓂` and `ex`

  * `guess` [Type: `Dict{Symbol, <:Real}, Dict{String, <:Real}}`]: Guess for the non-stochastic steady state. The keys must be the variable (and calibrated parameters) names and the values the guesses. Missing values are filled with standard starting values.
  * `verbose` [Default: `false`, Type: `Bool`]: print more information about how the non stochastic steady state is solved
  * `silent` [Default: `false`, Type: `Bool`]: do not print any information
  * `symbolic` [Default: `false`, Type: `Bool`]: try to solve the non stochastic steady state symbolically and fall back to a numerical solution if not possible
  * `perturbation_order` [Default: `1`, Type: `Int`]: take derivatives only up to the specified order at this stage. In case you want to work with higher order perturbation later on, respective derivatives will be taken at that stage.
  * `simplify` [Default: `true`, Type: `Bool`]: whether to elminiate redundant variables and simplify the non stochastic steady state (NSSS) problem. Setting this to `false` can speed up the process, but might make it harder to find the NSSS. If the model does not parse at all (at step 1 or 2), setting this option to `false` might solve it.

# Examples

```julia
using MacroModelling

@model RBC begin
    1  /  c[0] = (β  /  c[1]) * (α * exp(z[1]) * k[0]^(α - 1) + (1 - δ))
    c[0] + k[0] = (1 - δ) * k[-1] + q[0]
    q[0] = exp(z[0]) * k[-1]^α
    z[0] = ρ * z[-1] + std_z * eps_z[x]
end

@parameters RBC verbose = true begin
    std_z = 0.01
    ρ = 0.2
    δ = 0.02
    α = 0.5
    β = 0.95
end

@model RBC_calibrated begin
    1  /  c[0] = (β  /  c[1]) * (α * exp(z[1]) * k[0]^(α - 1) + (1 - δ))
    c[0] + k[0] = (1 - δ) * k[-1] + q[0]
    q[0] = exp(z[0]) * k[-1]^α
    z[0] = ρ * z[-1] + std_z * eps_z[x]
end

@parameters RBC_calibrated verbose = true guess = Dict(:k => 3) begin
    std_z = 0.01
    ρ = 0.2
    δ = 0.02
    k[ss] / q[ss] = 2.5 | α
    β = 0.95
end
```

# Programmatic model writing

Variables and parameters indexed with curly braces can be either referenced specifically (e.g. `c{H}[ss]`) or generally (e.g. `alpha`). If they are referenced generaly the parse assumes all instances (indices) are meant. For example, in a model where `alpha` has two indices `H` and `F`, the expression `alpha = 0.3` is interpreted as two expressions: `alpha{H} = 0.3` and `alpha{F} = 0.3`. The same goes for calibration equations.
