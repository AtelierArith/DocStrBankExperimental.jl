Parses the model equations and assigns them to an object.

# Arguments

  * `𝓂`: name of the object to be created containing the model information.
  * `ex`: equations

# Optional arguments to be placed between `𝓂` and `ex`

  * `max_obc_horizon` [Default: `40`, Type: `Int`]: maximum length of anticipated shocks and corresponding unconditional forecast horizon over which the occasionally binding constraint is to be enforced. Increase this number if no solution is found to enforce the constraint.

Variables must be defined with their time subscript in square brackets. Endogenous variables can have the following:

  * present: `c[0]`
  * non-stcohastic steady state: `c[ss]` instead of `ss` any of the following is also a valid flag for the non-stochastic steady state: `ss`, `stst`, `steady`, `steadystate`, `steady_state`, and the parser is case-insensitive (`SS` or `sTst` will work as well).
  * past: `c[-1]` or any negative Integer: e.g. `c[-12]`
  * future: `c[1]` or any positive Integer: e.g. `c[16]` or `c[+16]`

Signed integers are recognised and parsed as such.

Exogenous variables (shocks) can have the following:

  * present: `eps_z[x]` instead of `x` any of the following is also a valid flag for exogenous variables: `ex`, `exo`, `exogenous`, and the parser is case-insensitive (`Ex` or `exoGenous` will work as well).
  * past: `eps_z[x-1]`
  * future: `eps_z[x+1]`

Parameters enter the equations without square brackets.

If an equation contains a `max` or `min` operator, then the default dynamic (first order) solution of the model will enforce the occasionally binding constraint. You can choose to ignore it by setting `ignore_obc = true` in the relevant function calls.

# Examples

```julia
using MacroModelling

@model RBC begin
    1  /  c[0] = (β  /  c[1]) * (α * exp(z[1]) * k[0]^(α - 1) + (1 - δ))
    c[0] + k[0] = (1 - δ) * k[-1] + q[0]
    q[0] = exp(z[0]) * k[-1]^α
    z[0] = ρ * z[-1] + std_z * eps_z[x]
end
```

# Programmatic model writing

Parameters and variables can be indexed using curly braces: e.g. `c{H}[0]`, `eps_z{F}[x]`, or `α{H}`.

`for` loops can be used to write models programmatically. They can either be used to generate expressions where you iterate over the time index or the index in curly braces:

  * generate equation with different indices in curly braces: `for co in [H,F] C{co}[0] + X{co}[0] + Z{co}[0] - Z{co}[-1] end = for co in [H,F] Y{co}[0] end`
  * generate multiple equations with different indices in curly braces: `for co in [H, F] K{co}[0] = (1-delta{co}) * K{co}[-1] + S{co}[0] end`
  * generate equation with different time indices: `Y_annual[0] = for lag in -3:0 Y[lag] end` or `R_annual[0] = for operator = :*, lag in -3:0 R[lag] end`
