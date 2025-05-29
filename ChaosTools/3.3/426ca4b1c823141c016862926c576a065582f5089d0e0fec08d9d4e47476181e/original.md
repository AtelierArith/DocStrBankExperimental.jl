```
lyapunov(ds::DynamicalSystem, Τ; kwargs...) -> λ
```

Calculate the maximum Lyapunov exponent `λ` using a method due to Benettin [^Benettin1976], which simply evolves two neighboring trajectories (one called "given" and one called "test") while constantly rescaling the test one.

`T`  denotes the total time of evolution (should be `Int` for discrete time systems).

See also [`lyapunovspectrum`](@ref), [`local_growth_rates`](@ref).

## Keyword arguments

  * `show_progress = false`: Display a progress bar of the process.
  * `u0 = initial_state(ds)`: Initial condition.
  * `Ttr = 0`: Extra "transient" time to evolve the trajectories before starting to measure the exponent. Should be `Int` for discrete systems.
  * `d0 = 1e-9`: Initial & rescaling distance between the two neighboring trajectories.
  * `d0_lower = 1e-3*d0`: Lower distance threshold for rescaling.
  * `d0_upper = 1e+3*d0`: Upper distance threshold for rescaling.
  * `Δt = 1`: Time of evolution between each check rescaling of distance.
  * `inittest = (u1, d0) -> u1 .+ d0/sqrt(length(u1))`: A function that given `(u1, d0)` initializes the test state with distance `d0` from the given state `u1`  (`D` is the dimension of the system). This function can be used when you want to avoid the test state appearing in a region of the phase-space where it would have e.g. different energy or escape to infinity.

## Description

Two neighboring trajectories with initial distance `d0` are evolved in time. At time $t_i = t_{i-1} + \Delta t$, if their distance $d(t_i)$ either exceeds the `d0_upper`, or is lower than `d0_lower`, the test trajectory is rescaled back to having distance `d0` from the reference one, while the rescaling keeps the difference vector along the maximal expansion/contraction direction: $u_2 \to u_1+(u_2−u_1)/(d(t_i)/d_0)$.

The maximum Lyapunov exponent is the average of the time-local Lyapunov exponents

$$
\lambda = \frac{1}{t_{n} - t_0}\sum_{i=1}^{n}
\ln\left( a_i \right),\quad a_i = \frac{d(t_{i})}{d_0}.
$$

## Performance notes

This function simply initializes a [`ParallelDynamicalSystem`](@ref) and calls the method below.

The reason we only conditionally rescale the neighboring trajectories is computational: the averaging will give correct result overall if the trajectories never diverge or converge (i.e., for periodic orbits).

[^Benettin1976]: G. Benettin *et al.*, Phys. Rev. A **14**, pp 2338 (1976)
