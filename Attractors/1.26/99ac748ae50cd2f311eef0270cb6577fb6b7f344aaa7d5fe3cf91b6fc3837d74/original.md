```
edgetracking(ds::DynamicalSystem, attractors::Dict; kwargs...)
```

Track along a basin boundary in a dynamical system `ds` with two or more attractors in order to find an *edge state*. Results are returned in the form of [`EdgeTrackingResults`](@ref), which contains the pseudo-trajectory `edge` representing the track on the basin boundary, along with additional output (see below).

The system's `attractors` are specified as a `Dict` of `StateSpaceSet`s, as in [`AttractorsViaProximity`](@ref) or the output of [`extract_attractors`](@ref). By default, the algorithm is initialized from the first and second attractor in `attractors`. Alternatively, the initial states can be set via keyword arguments `u1`, `u2` (see below). Note that the two initial states must belong to different basins of attraction.

## Keyword arguments

  * `bisect_thresh = 1e-7`: distance threshold for bisection.
  * `diverge_thresh = 1e-6`: distance threshold for parallel integration.
  * `u1`: first initial state (defaults to first point in first entry of `attractors`).
  * `u2`: second initial state (defaults to first point in second entry of `attractors`).
  * `maxiter = 100`: maximum number of iterations before the algorithm stops.
  * `abstol = 1e-9`: distance threshold for convergence of the updated edge state.
  * `T_transient = 0.0`: transient time before the algorithm starts saving the edge track.
  * `tmax = Inf`: maximum integration time of parallel trajectories until re-bisection.
  * `Δt = 0.01`: time step passed to [`step!`](@ref) when evolving the two trajectories.
  * `show_progress = true`: if true, shows progress bar and information while running.
  * `verbose = true`: if false, silences print output and warnings while running.
  * `kw...`: additional keyword arguments to be passed to [`AttractorsViaProximity`](@ref). We strongly recommend to either pass in a high `Ttr`, or a very small `ε`, (smaller than the default estimated by [`AttractorsViaProximity`](@ref)) to avoid transient parts of trajectories wrongly being classified as having converged.

## Description

The edge tracking algorithm is a numerical method to find an *edge state* or (possibly chaotic) saddle on the boundary between two basins of attraction. Introduced by [Battelino1988](@cite) and further described by [Skufca2006](@cite), the algorithm has been applied to, e.g., the laminar-turbulent boundary in plane Couette flow [Schneider2008](@cite), Wada basins [Wagemakers2020](@cite), as well as Melancholia states in conceptual [Mehling2023](@cite) and intermediate-complexity [Lucarini2017](@cite) climate models. Relying only on forward integration of the system, it works even in high-dimensional systems with complicated fractal basin boundary structures.

The algorithm consists of two main steps: bisection and tracking. First, it iteratively bisects along a straight line in state space between the intial states `u1` and `u2` to find the separating basin boundary. The bisection stops when the two updated states are less than `bisect_thresh` (Euclidean distance in state space) apart from each other. Next, a `ParallelDynamicalSystem` is initialized from these two updated states and integrated forward until the two trajectories diverge from each other by more than `diverge_thresh` (Euclidean distance). The two final states of the parallel integration are then used as new states `u1` and `u2` for a new bisection, and so on, until a stopping criterion is fulfilled.

Two stopping criteria are implemented via the keyword arguments `maxiter` and `abstol`. Either the algorithm stops when the number of iterations reaches `maxiter`, or when the state space position of the updated edge point changes by less than `abstol` (in Euclidean distance) compared to the previous iteration. Convergence below `abstol` happens after sufficient iterations if the edge state is a saddle point. However, the edge state may also be an unstable limit cycle or a chaotic saddle. In these cases, the algorithm will never actually converge to a point but (after a transient period) continue populating the set constituting the edge state by tracking along it.

A central idea behind this algorithm is that basin boundaries are typically the stable manifolds of unstable sets, namely edge states or saddles. The flow along the basin boundary will thus lead to these sets, and the iterative bisection neutralizes the unstable direction of the flow away from the basin boundary. If the system possesses multiple edge states, the algorithm will find one of them depending on where the initial bisection locates the boundary.

## Output

Returns a data type [`EdgeTrackingResults`](@ref) containing the results.

Sometimes, the AttractorMapper used in the algorithm may erroneously identify both states `u1` and `u2` with the same basin of attraction due to being very close to the basin boundary. If this happens, a warning is raised and `EdgeTrackingResults.success = false`.
