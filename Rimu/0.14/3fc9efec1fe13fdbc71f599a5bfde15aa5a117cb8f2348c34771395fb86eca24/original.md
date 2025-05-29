```
ProjectorMonteCarloProblem(hamiltonian::AbstractHamiltonian; kwargs...)
```

Defines a problem to be solved by projector quantum Monte Carlo (QMC) methods, such as the the [`FCIQMC`](@ref) algorithm.

# Common keyword arguments and defaults:

  * `time_step = 0.01`: Initial time step size.
  * `last_step = 100`: Controls the number of steps.
  * `target_walkers = 1_000`: Target for the 1-norm of the coefficient vector.
  * `start_at = starting_address(hamiltonian)`: Define the initial state vector(s).   An $r × s$ matrix of state vectors can be passed where $r$ is the   number of replicas and $s$ the number of spectral states. See also   [`default_starting_vector`](@ref).
  * `style = IsDynamicSemistochastic()`: The [`StochasticStyle`](@ref) of the simulation.
  * `initiator = false`: Whether to use initiators. Can be `true`, `false`, or a valid   [`InitiatorRule`](@ref).
  * `threading`: Default is to use multithreading and/or [MPI](https://juliaparallel.org/MPI.jl/latest/) if available. Set to `true` to force [`PDVec`](@ref) for the starting vector, `false` for serial computation; may be overridden by `start_at`.
  * `reporting_strategy = ReportDFAndInfo()`: How and when to report results, see [`ReportingStrategy`](@ref).
  * `post_step_strategy = ()`: Extract observables (e.g. [`ProjectedEnergy`](@ref)), see [`PostStepStrategy`](@ref).
  * `n_replicas = 1`: Number of synchronised independent simulations.
  * `replica_strategy = NoStats(n_replicas)`: Which results to report from replica simulations, see [`ReplicaStrategy`](@ref).
  * `n_spectral = 1`: Number of targeted spectral states. Set `n_spectral > 1` to find excited states.
  * `spectral_strategy = GramSchmidt(n_spectral)`: The [`SpectralStrategy`](@ref) used for orthogonalizing spectral states.

# Example

```jldoctest
julia> hamiltonian = HubbardReal1D(BoseFS(1,2,3));

julia> problem = ProjectorMonteCarloProblem(hamiltonian; target_walkers = 500, last_step = 100);

julia> simulation = solve(problem);

julia> simulation.success[]
true

julia> size(DataFrame(simulation))
(100, 9)
```

# Further keyword arguments:

  * `starting_step = 1`: Starting step of the simulation.
  * `wall_time = Inf`: Maximum time allowed for the simulation.
  * `simulation_plan = SimulationPlan(; starting_step, last_step, wall_time)`: Defines the   duration of the simulation. Takes precedence over `last_step` and `wall_time`.
  * `ζ = 0.08`: Damping parameter for the shift update.
  * `ξ = ζ^2/4`: Forcing parameter for the shift update.
  * `shift_strategy = DoubleLogUpdate(; target_walkers, ζ, ξ)`: How to update the `shift`,   see [`ShiftStrategy`](@ref).
  * `time_step_strategy = ConstantTimeStep()`: Adjust time step or not, see   `TimeStepStrategy`.
  * `algorithm = FCIQMC(; shift_strategy, time_step_strategy)`: The algorithm to use.   Currenlty only [`FCIQMC`](@ref) is implemented.
  * `shift`: Initial shift value or collection of shift values. Determined by default from the   Hamiltonian and the starting vectors.
  * `initial_shift_parameters`: Initial shift parameters or collection of initial shift   parameters. Overrides `shift` if provided.
  * `max_length = 2 * target_walkers + 100`: Maximum length of the vectors.
  * `display_name = "PMCSimulation"`: Name displayed in progress bar (via `ProgressLogging`).
  * `metadata`: User-supplied metadata to be added to the report. Must be an iterable of pairs or a `NamedTuple`, e.g. `metadata = ("key1" => "value1", "key2" => "value2")`. All metadata is converted to strings.
  * `random_seed = true`: Provide and store a seed for the random number generator. If set to   `true`, a new random seed is generated from `RandomDevice()`. If set to number, this   number is used as the seed. This seed is used by `solve` (and `init`) to re-seed the   default random number generator (consistently on each MPI rank) such that   `solve`ing the same `ProjectorMonteCarloProblem` twice will yield identical results. If   set to `false`, no seed is used and consecutive random numbers are used.
  * `minimum_size = 2*num_spectral_states(spectral_strategy)`: The minimum size of the basis   used to construct starting vectors for simulations of spectral states, if `start_at`   is not provided.

See also [`init`](@ref), [`solve`](@ref).
