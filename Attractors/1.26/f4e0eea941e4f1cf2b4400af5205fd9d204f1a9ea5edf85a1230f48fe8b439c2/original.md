```
AttractorsViaRecurrences(ds::DynamicalSystem, grid; kwargs...)
```

Map initial conditions of `ds` to attractors by identifying attractors on the fly based on recurrences in the state space, as outlined in [Datseris2022](@cite). However, the Description section below for has a more accurate (and simpler) exposition to the algorithm than the paper.

`grid` is instructions for partitioning the state space into finite-sized cells so that a finite state machine can operate on top of it. Possibilities are:

1. A tuple of sorted `AbstractRange`s for a regular grid.

Example is `grid = (xg, yg)` where `xg = yg = range(-5, 5; length = 100)`   for a two-dimensional system.

2. A tuple of sorted `AbstractVector`s for an irregular grid, for example

`grid = (xg, yg)` with `xg = range(0, 10.0^(1/2); length = 200).^2,   yg = range(-5, 5; length = 100)`.

3. An instance of the special grid type

[`SubdivisionBasedGrid`](@ref), which can be created either manually or by using   [`subdivision_based_grid`](@ref).   This automatically analyzes and adapts grid discretization   levels in accordance with state space flow speed in different regions.

The grid has to be the same dimensionality as the state space, use a [`ProjectedDynamicalSystem`](@ref) if you want to search for attractors in a lower dimensional subspace.

## Keyword arguments

  * `sparse = true`: control the storage type of the state space grid. If true,  uses a sparse array, whose memory usage is in general more efficient than a regular  array obtained with `sparse=false`. In practice, the sparse representation should  always be preferred when searching for [`basins_fractions`](@ref). Only for very low  dimensional systems and for computing the full [`basins_of_attraction`](@ref) the  non-sparse version should be used.

### Time evolution configuration

  * `Ttr = 0`: Skip a transient before the recurrence routine begins.
  * `Δt`: Approximate integration time step (second argument of the `step!` function). The keyword `Dt` can also be used instead if `Δ` (`\Delta`) is not accessible. It is `1` for discrete time systems. For continuous systems, an automatic value is calculated using [`automatic_Δt_basins`](@ref). For very fine grids, this can become very small, much smaller than the typical integrator internal step size in case of adaptive integrators. In such cases, use `stop_at_Δt = true`.
  * `stop_at_Δt = false`: Only used if the input dynamical system is `CoupledODEs`. It is given as a third input to `step!`. Value `true` is useful in (1) very fine grids, and (2) if some of the attractors are limit cycles. We have noticed that in this case the integrator timestep becomes commensurate with the limit cycle period, leading to incorrectly counting the limit cycle as more than one attractor. `stop_at_Δt = true` should also be used if you want an accurate estimate of [`convergence_time`](@ref).

### Finite state machine configuration

  * `consecutive_recurrences = 100`: Number of consecutive visits to previously visited unlabeled cells (i.e., recurrences) required before declaring we have converged to a new attractor. This number tunes the accuracy of converging to attractors and should generally be high (and even higher for chaotic systems).
  * `attractor_locate_steps = 1000`: Number of subsequent steps taken to locate accurately the new attractor after the convergence phase is over. Once `attractor_locate_steps` steps have been taken, the new attractor has been identified with sufficient accuracy and iteration stops. This number can be very high without much impact to overall performance.
  * `store_once_per_cell = true`: Control if multiple points in state space that belong to the same cell are stored or not in the attractor, when a new attractor is found. If `true`, each visited cell will only store a point once, which is desirable for fixed points and limit cycles. If `false` then `attractor_locate_steps` points are stored per attractor, leading to more densely stored attractors, which may be desirable for instance in chaotic attractors.
  * `consecutive_attractor_steps = 2`: Μaximum checks of consecutives hits of an existing attractor cell before declaring convergence to that existing attractor.
  * `consecutive_basin_steps = 10`: Number of consecutive visits of the same basin of attraction required before declaring convergence to an existing attractor. This is ignored if `sparse = true`, as basins are not stored internally in that case.
  * `consecutive_lost_steps = 20`: Maximum check of iterations outside the defined grid before we declare the orbit lost outside and hence assign it label `-1`.
  * `horizon_limit = 1e6`: If the norm of the integrator state reaches this limit we declare that the orbit diverged to infinity.
  * `maximum_iterations = Int(1e6)`: A safety counter that is always increasing for each initial condition. Once exceeded, the algorithm assigns `-1` and throws a warning. This clause exists to stop the algorithm never halting for inappropriate grids. It may happen when a newly found attractor orbit intersects in the same cell of a previously found attractor (which leads to infinite resetting of all counters).

## Description

An initial condition given to an instance of `AttractorsViaRecurrences` is iterated based on the integrator corresponding to `ds`. Enough recurrences in the state space (i.e., a trajectory visited a region it has visited before) means that the trajectory has converged to an attractor. This is the basis for finding attractors.

A finite state machine (FSM) follows the trajectory in the state space, and constantly maps it to a cell in the given `grid`. The grid cells store information: they are empty, visited, basins, or attractor cells. The state of the FSM is decided based on the cell type and the previous state of the FSM. Whenever the FSM recurs its state, its internal counter is increased, otherwise it is reset to 0. Once the internal counter reaches a threshold, the FSM terminates or changes its state. The possibilities for termination are the following:

  * The trajectory hits `consecutive_recurrences` times in a row previously visited cells:  it is considered that an attractor is found and is labelled with a new ID. Then,  iteration continues for `attractor_locate_steps` steps. Each cell visited in this period stores  the "attractor" information. Then iteration terminates and the initial condition is  numbered with the attractor's ID.
  * The trajectory hits an already identified attractor `consecutive_attractor_steps` consecutive times:  the initial condition is numbered with the attractor's basin ID.
  * The trajectory hits a known basin `consecutive_basin_steps` times in a row: the initial condition  belongs to that basin and is numbered accordingly. Notice that basins are stored and  used only when `sparse = false` otherwise this clause is ignored.
  * The trajectory spends `consecutive_lost_steps` steps outside the defined grid or the norm  of the dynamical system state becomes > than `horizon_limit`: the initial  condition is labelled `-1`.
  * If none of the above happens, the initial condition is labelled `-1` after  `maximum_iterations` steps.

There are some special internal optimizations and details that we do not describe here but can be found in comments in the source code. (E.g., a special timer exists for the "lost" state which does not interrupt the main timer of the FSM.)

A video illustrating how the algorithm works can be found in the online documentation, under the [recurrences animation](@ref recurrences_animation) page.
