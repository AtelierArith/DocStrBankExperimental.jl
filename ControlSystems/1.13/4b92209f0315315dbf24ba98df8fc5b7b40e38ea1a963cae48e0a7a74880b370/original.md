```
res = lsim(sys::DelayLtiSystem, u, t::AbstractArray{<:Real}; x0=fill(0.0, nstates(sys)), alg=MethodOfSteps(Tsit5()), abstol=1e-6, reltol=1e-6, force_dtmin=true, kwargs...)
```

Simulate system `sys`, over time `t`, using input signal `u`, with initial state `x0`, using method `alg` .

Arguments:

`t`: Has to be an `AbstractVector` with equidistant time samples (`t[i] - t[i-1]` constant) `u`: Function to determine control signal `ut` at a time `t`, on any of the following forms:

  * `u`: Function to determine control signal `uₜ` at a time `t`, on any of the following forms:

      * A constant `Number` or `Vector`, interpreted as a constant input.
      * Function `u(x, t)` that takes the internal state and time, note, the state representation for delay systems is not the same as for rational systems.
      * In-place function `u(uₜ, x, t)`. (Slightly more efficient)

`alg, abstol, reltol` and `kwargs...`: are sent to `DelayDiffEq.solve`.

This methods sets `force_dtmin=true` by default to handle the discontinuity implied by, e.g., step inputs. This may lead to the solver taking a long time to solve ill-conditioned problems rather than exiting early with a warning.

Returns an instance of [`SimResult`](@ref) which can be plotted directly or destructured into `y, t, x, u = res`.
