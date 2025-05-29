```
exit_entry_times(ds::DynamicalSystem, u₀, εs, T; kwargs...) → exits, entries
```

Collect exit and entry times for balls or boxes centered at `u₀` with radii `εs`, in the state space of the given dynamical system. Return the exit and (re-)entry return times to the set(s), where each of these is a vector containing all collected times for the respective `ε`-radius set, for `ε ∈ εs`. The dynamical system is evolved up to `T` total time.

Use `transit_return_times(exits, entries)` to transform the output into transit and return times, and see also [`mean_return_times`](@ref).

The keyword `show_progress` displays a progress bar. It is `false` for discrete and `true` for continuous systems by default.

## Description

Transit and return time statistics are important for the transport properties of dynamical systems[^Meiss1997] and can be connected with fractal dimensions of chaotic sets[^Boev2014].

The current algorithm collects exit and re-entry times to given sets in the state space, which are centered at the state `u₀`. **The system evolution always starts from `u₀`** and the initial state of `ds` is irrelevant. `εs` is always a `Vector`.

### Specification of sets to return to

If each entry of `εs` is a real number, then sets around `u₀` are nested hyper-spheres of radius `ε ∈ εs`. The sets can also be hyper-rectangles (boxes), if each entry of `εs` is a vector itself. Then, the `i`-th box is defined by the space covered by `u0 .± εs[i]` (thus the actual box size is `2εs[i]`!). In the future, state space sets will be specified more conveniently and a single argument `sets` will be given instead of `u₀, εs`.

The reason to input multiple `εs` at once is purely for performance optimization (much faster than doing each `ε` individually).

### Discrete time systems

For discrete systems, exit time is recorded immediately after exiting of the set, and re-entry is recorded immediately on re-entry. This means that if an orbit needs 1 step to leave the set and then it re-enters immediately on the next step, the return time is 1.

### Continuous time systems

For continuous systems, a steppable integrator supporting interpolation is used. The way to specify how to estimate exit and entry times is via the keyword `crossing_method` whose values can be:

1. `CrossingLinearIntersection()`: Linear interpolation is used between integrator steps and the intersection between lines and spheres is used to find the crossing times.
2. `CrossingAccurateInterpolation(; abstol=1e-12, reltol=1e-6)`: Extremely accurate high order interpolation is used between integrator steps. First, a minimization with Optim.jl finds the minimum distance of the trajectory to the set center. Then, Roots.jl is used to find the exact crossing point. The tolerances are given to both procedures.

Clearly, `CrossingAccurateInterpolation` is much more accurate than `CrossingLinearIntersection`, but also much slower. However, the smaller the steps the integrator takes (in case some very high accuracy solver is used), the closer the linear intersection gets to the accurate version. Benchmarks are advised for the individual specific case the algorithm is applied at, in order to choose the best method.

The keyword `threshold_distance = Inf` provides a means to skip the interpolation check, if the current state of the integrator is too far from the set center. If the distance of the current state of the integrator is `threshold_distance` or more distance away from the set center, attempts to interpolate are skipped. By default `threshold_distance = Inf` and hence this never happens. Typically you'd want this to be 10-100 times the distance the trajectory covers at an average integrator step.

[^Meiss1997]: Meiss, J. D. *Average exit time for volume-preserving maps*, [Chaos (1997)](https://doi.org/10.1063/1.166245)

[^Boev2014]: Boev, Vadivasova, & Anishchenko, *Poincaré recurrence statistics as an indicator of chaos synchronization*, [Chaos (2014)](https://doi.org/10.1063/1.4873721)
