```julia
struct VariableRateJump{R, F, R2, R3, R4, I, T, T2} <: JumpProcesses.AbstractJump
```

Defines a jump process with a rate (i.e. hazard, intensity, or propensity) that may explicitly depend on time. More precisely, one where the rate function is allowed to change *between* the occurrence of jumps. For detailed examples and usage information, see the

  * [Tutorial](https://docs.sciml.ai/JumpProcesses/stable/tutorials/discrete_stochastic_example/)

Note that two types of `VariableRateJump`s are currently supported, with different performance characteritistics.

  * A general `VariableRateJump` or `VariableRateJump` will refer to one in which only `rate` and `affect` functions are specified.

      * These are the most general in what they can represent, but require the use of an `ODEProblem` or `SDEProblem` whose underlying timestepper handles their evolution in time (via the callback interface).
      * This is the least performant jump type in simulations.
  * Bounded `VariableRateJump`s require passing the keyword arguments `urate` and `rateinterval`, corresponding to functions `urate(u, p, t)` and `rateinterval(u, p, t)`, see below. These must calculate a time window over which the rate function is bounded by a constant. Note that it is ok if the rate bound would be violated within the time interval due to a change in `u` arising from another `ConstantRateJump`, `MassActionJump` or *bounded* `VariableRateJump` being executed, as the chosen aggregator will then handle recalculating the rate bound and interval. *However, if the bound could be violated within the time interval due to a change in `u` arising from continuous dynamics such as a coupled ODE, SDE, or a general `VariableRateJump`, bounds should not be given.* This ensures the jump is classified as a general `VariableRateJump` and properly handled. One can also optionally provide a lower bound function, `lrate(u, p, t)`, via the `lrate` keyword argument. This can lead to increased performance. The validity of the lower bound should hold under the same conditions and rate interval as `urate`.

      * Bounded `VariableRateJump`s can currently be used in the `Coevolve` aggregator, and can therefore be efficiently simulated in pure-jump `DiscreteProblem`s using the `SSAStepper` time-stepper.
      * These can be substantially more performant than general `VariableRateJump`s without the rate bound functions.

Reemphasizing, the additional user provided functions leveraged by bounded `VariableRateJumps`, `urate(u, p, t)`, `rateinterval(u, p, t)`, and the optional `lrate(u, p, t)` require that

  * For `s` in `[t, t + rateinterval(u, p, t)]`, we have that `lrate(u, p, t) <= rate(u, p, s) <= urate(u, p, t)`.
  * It is ok if these bounds would be violated during the time window due to another `ConstantRateJump`, `MassActionJump` or bounded `VariableRateJump` occurring. However, they must remain valid if `u` changes for any other reason (for example, due to continuous dynamics like ODEs, SDEs, or general `VariableRateJump`s).

## Fields

  * `rate`: Function `rate(u,p,t)` that returns the jump's current rate given state `u`, parameters `p` and time `t`.
  * `affect!`: Function `affect!(integrator)` that updates the state for one occurrence of the jump given `integrator`.
  * `lrate`: Optional function `lrate(u, p, t)` that computes a lower bound on the rate in the interval `t` to `t + rateinterval(u, p, t)` at time `t` given state `u` and parameters `p`. This bound must rigorously hold during the time interval as long as another `ConstantRateJump`, `MassActionJump`, or *bounded* `VariableRateJump` has not been sampled. When using aggregators that support bounded `VariableRateJump`s, currently only `Coevolve`, providing a lower-bound can lead to improved performance.

  * `urate`: Optional function `urate(u, p, t)` for general `VariableRateJump`s, but is required to define a bounded `VariableRateJump`, which can be used with supporting aggregators,  currently only `Coevolve`, and offers improved computational performance. Computes an upper bound for the rate in the interval `t` to `t + rateinterval(u, p, t)` at time `t` given state `u` and parameters `p`. This bound must rigorously hold during the time interval as long as another `ConstantRateJump`, `MassActionJump`, or *bounded* `VariableRateJump` has not been sampled.
  * `rateinterval`: Optional function `rateinterval(u, p, t)` for general `VariableRateJump`s, but is required to define a bounded `VariableRateJump`, which can be used with supporting  aggregators, currently only `Coevolve`, and offers improved computational performance. Computes the time interval from time `t` over which the `urate` and `lrate` bounds will hold, `t` to `t + rateinterval(u, p, t)`, given state `u` and parameters `p`. This bound must rigorously hold during the time interval as long as another `ConstantRateJump`, `MassActionJump`, or *bounded* `VariableRateJump` has not been sampled.
  * `idxs`
  * `rootfind`
  * `interp_points`
  * `save_positions`
  * `abstol`
  * `reltol`

## Examples

Suppose `u[1]` gives the number of particles and `t*p[1]` the probability per time each particle can decay away. A corresponding `VariableRateJump` for this jump process is

```julia
rate(u,p,t) = t*p[1]*u[1]
affect!(integrator) = integrator.u[1] -= 1
vrj = VariableRateJump(rate, affect!)
```

To define a bounded `VariableRateJump` that can be used with supporting aggregators such as `Coevolve`, we must define bounds and a rate interval:

```julia
rateinterval(u,p,t) = (1 / p[1]) * 2
rate(u,p,t) = t * p[1] * u[1]
lrate(u, p, t) = rate(u, p, t)
urate(u,p,t) = rate(u, p, t + rateinterval(u,p,t))
affect!(integrator) = integrator.u[1] -= 1
vrj = VariableRateJump(rate, affect!; lrate = lrate, urate = urate,
                                      rateinterval = rateinterval)
```

## Notes

  * When using an aggregator that supports bounded `VariableRateJump`s, `DiscreteProblem` can be used. Otherwise, `ODEProblem` or `SDEProblem` must be used.
  * **When not using aggregators that support bounded `VariableRateJump`s, or when there are general `VariableRateJump`s, `integrator`s store an effective state type that wraps the main state vector.** See [`ExtendedJumpArray`](@ref) for details on using this object. In this case all `ConstantRateJump`, `VariableRateJump` and callback `affect!` functions receive an integrator with `integrator.u` an [`ExtendedJumpArray`](@ref).
  * Salis H., Kaznessis Y.,  Accurate hybrid stochastic simulation of a system of coupled chemical or biochemical reactions, Journal of Chemical Physics, 122 (5), DOI:10.1063/1.1835951 is used for calculating jump times with `VariableRateJump`s within ODE/SDE integrators.
