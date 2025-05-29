```
AttractorsViaProximity(ds::DynamicalSystem, attractors::Dict; kwargs...)
```

Map initial conditions to attractors based on whether the trajectory reaches `ε`-distance close to any of the user-provided `attractors`, which have to be in a form of a dictionary mapping attractor labels to `StateSpaceSet`s containing the attractors.

## Keywords

  * `ε = nothing`: Distance below which a trajectory has converged to an attractor, see below. Type `\varepsilon<TAB>` to input `ε`.
  * `Ttr = 0`: Transient time to first evolve the system for before checking for proximity.
  * `Δt = 1`: Step time given to `step!`.
  * `stop_at_Δt = false`: Third argument given to `step!`.
  * `horizon_limit = 1e3`: If the maximum distance of the trajectory from any of the given attractors exceeds this limit, it is assumed that the trajectory diverged (gets labelled as `-1`).
  * `consecutive_lost_steps = 10000`: If the `ds` has been stepped this many times without coming `ε`-near to any attractor,  it is assumed that the trajectory diverged (gets labelled as `-1`).
  * `distance = StrictlyMinimumDistance()`: Distance function for evaluating the distance between the trajectory end-point and the given attractors. Can be anything given to [`set_distance`](@ref).

## Description

The system gets stepped, and at each step the distance of the current state to all attractors is computed via `set_distance` using the `distance` keyword. If any of these distances is `< ε`, then the label of the nearest attractor is returned.

`attractors` do not have to be "true" attractors. Any arbitrary sets in the state space can be provided.

If an `ε::Real` is not provided by the user, a value is computed automatically as 1/10th of the minimum distance between all `attractors`. This operation can be expensive for large `StateSpaceSet`s. If `length(attractors) == 1`, then `ε` becomes 1/10 of the diagonal of the box containing the attractor. If `length(attractors) == 1` and the attractor is a single point, an error is thrown.

The [`convergence_time`](@ref) is `Inf` if an initial condition has not converged. As such, the convergence time is always a float type even for discrete time systems.
