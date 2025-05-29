```
lomc!(ham::AbstractHamiltonian, [v]; kwargs...) -> df, state
lomc!(state::ReplicaState, [df]; kwargs...) -> df, state
```

Linear operator Monte Carlo: Perform a projector quantum Monte Carlo simulation for determining the lowest eigenvalue of `ham`. The details of the simulation are controlled by the optional keyword arguments and by the type of the optional starting vector `v`. Alternatively, a `ReplicaState` can be passed in to continue a previous simulation.

# Common keyword arguments and defaults:

  * `laststep = 100` - controls the number of steps.
  * `dτ = 0.01` - time step.
  * `targetwalkers = 1000` - target for the 1-norm of the coefficient vector.
  * `address = starting_address(ham)` - set starting address for default `v` and `shift`.
  * `style = IsStochasticInteger()` - set [`StochasticStyle`](@ref) for default `v`; unused if `v` is specified.
  * `initiator = NonInitiator()` - set [`InitiatorRule`](@ref) for default `v`; unused if `v` is specified.
  * `threading` - default is to use multithreading and [MPI](https://juliaparallel.org/MPI.jl/latest/) if multiple threads are available. Set to `true` to force [`PDVec`](@ref) for the starting vector, `false` for serial computation; unused if `v` is specified.
  * `shift = diagonal_element(ham, address)` - initial value of shift.
  * `post_step_strategy::NTuple{N,<:PostStepStrategy} = ()` - extract observables (e.g. [`ProjectedEnergy`](@ref)), see [`PostStepStrategy`](@ref). (Deprecated: `post_step` is accepted as an alias for `post_step_strategy`.)
  * `replica_strategy::ReplicaStrategy = NoStats(1)` - run several synchronised simulations, see [`ReplicaStrategy`](@ref). (Deprecated: `replica` is accepted as an alias for `replica_strategy`.)
  * `reporting_strategy::ReportingStrategy = ReportDFAndInfo()` - how and when to report results, see [`ReportingStrategy`](@ref). (Deprecated: `r_strat` is accepted as an alias for `reporting_strategy`.)
  * `name = "lomc!"` - name displayed in progress bar (via `ProgressLogging`)
  * `metadata` - user-supplied metadata to be added to the report `df`. Must be an iterable of pairs or a `NamedTuple`, e.g. `metadata = ("key1" => "value1", "key2" => "value2")`. All metadata is converted to strings.

Some metadata is automatically added to the report `df` including [`Rimu.PACKAGE_VERSION`](@ref) and data from `state`.

# Return values

`lomc!` returns a named tuple with the following fields:

  * `df`: a `DataFrame` with all statistics being reported.
  * `state`: a `ReplicaState` that can be used for continuations.

# Example

```jldoctest
julia> address = BoseFS(1,2,3);

julia> hamiltonian = HubbardReal1D(address);

julia> df1, state = @suppress lomc!(hamiltonian; targetwalkers=500, laststep=100);

julia> df2, _ = @suppress lomc!(state, df1; laststep=200, metadata=(;info="cont")); # Continuation run

julia> size(df1)
(100, 9)

julia> size(df2)
(200, 9)

julia> using DataFrames; metadata(df2, "info") # retrieve custom metadata
"cont"

julia> metadata(df2, "hamiltonian") # some metadata is automatically added
"HubbardReal1D(fs\"|1 2 3⟩\"; u=1.0, t=1.0)"
```

# Further keyword arguments and defaults:

  * `τ_strat::TimeStepStrategy = ConstantTimeStep()` - adjust time step or not, see [`TimeStepStrategy`](@ref)
  * `s_strat::ShiftStrategy = DoubleLogUpdate(; target_walkers=targetwalkers, ζ = 0.08, ξ = ζ^2/4)` - how to update the `shift`, see [`ShiftStrategy`](@ref).
  * `maxlength = 2 * s_strat.target_walkers + 100` - upper limit on the length of `v`; when reached, `lomc!` will abort
  * `wm` - working memory for re-use in subsequent calculations; is mutated.
  * `df = DataFrame()` - when called with `AbstractHamiltonian` argument, a `DataFrame` can be passed for merging with the report `df`.

The default choice for the starting vector is `v = default_starting_vector(; address, style, threading, initiator)`. See [`default_starting_vector`](@ref), [`PDVec`](@ref), [`DVec`](@ref), [`StochasticStyle`](@ref), and [`InitiatorRule`](@ref).

!!! warning
    The use of this `lomc!` is deprecated. Use [`ProjectorMonteCarloProblem`](@ref) and [`solve`](@ref) instead.

