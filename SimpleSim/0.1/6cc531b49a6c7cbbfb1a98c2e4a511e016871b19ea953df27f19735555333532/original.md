```
simulate(model; kwargs...)
```

Runs the simulation for the given `model`.

Returns a `NamedTuple` with all time-series information about the simulation.

# Mandatory Keyword Arguments

  * `T`: Total time of the simulation. Mand

# Optional Keyword Arguments

  * `uc`: Expects a function `(t) -> u` defining the input to a continuous-time model at time `t`. Defaults to `(t) -> nothing`.
  * `ud`: Expects a function `(t) -> u` defining the input to a discrete-time model at time `t`. Defaults to `(t) -> nothing`.
  * `Δt_max`: Maximum step size used for continuous-time model integration. Defaults to `ΔT_DEFAULT` set in `SimpleSim.jl`.
  * `t0`: Initial time. Defaults to `0 // 1`.
  * `xc0`: Initial state for continuous-time model. Overwrites any initial state defined in the model itself. Defaults to `nothing`.
  * `xd0`: Initial state for discrete-time model. Overwrites any initial state defined in the model itself. Defaults to `nothing`.
  * `integrator`: Integration method to be used for continuous-time models. See below for supported integrators. Defaults to `RK4.`
  * `options`: See below for additional options that can be set.

# Supported Numerical Integration Methods

These options can be passed to the `simulate` function as the `integrator` keyword argument:

```julia
@enum SimpleSimIntegrator RK4 = 1 Euler = 2 Heun = 3 RKF45 = 4
```

# Options

`SimpleSim.jl` has a few default parameters for running simulations that generally do not need to be changed. However, if necessary the following options can be passed in a `NamedTuple` to the `options` keyword argument.

  * `Δt_default`: replaces the default (maximum) step size used for continuous-time integration. Should be rational.   Defaults to global parameter `ΔT_DEFAULT`.
  * `Δt_min`: replaces the minimum step size used for continuous-time integration. Especially relevant for adaptive step size integrators.   Defaults to `1 // 1_000_000`.
  * `zero_crossing_tol`: absolute tolerance used when computing the time of a zero-crossing.   Defaults to `1e-5`.
  * `RKF45_rel_tol`: relative tolerance between the truncation error and the 5th order Runge-Kutta estimate leading to termination of the `RKF45` integrator.   Defaults to `1e-6`.
  * `RKF45_abs_tol`: absolute tolerance for the truncation error leading to termination of the `RKF45` integrator.   Defaults to `1e-7`.
  * `silent`: if set to `true` all output, including warnings and erros is disabled.   To only print erros and warnings and disable all other output set `display_progress` and `debug` to `false`.   Defaults to `false`.
  * `debug`: set to `true` to get additional information printed in the terminal that might help you debug your models.   Defaults to `false`.
  * `display_progress`: set to `false` if you don't want to be updated about simulation progress in the terminal.   Defaults to `true`.
  * `progress_spacing`: time between progress updates in the terminal.   Defaults to `1 // 1`.
  * `base_rng`: random number generator used for random draw functions.   Defaults to `MersenneTwister`.
  * `out_stream`: IO stream used for console output.   Defaults to `stdout`.

# Example with Options

```julia
out = simulate(my_model,
    T = 20 // 1,
    options = (
        silent = true,
        base_rng = Xoshiro,
    )
)
```
