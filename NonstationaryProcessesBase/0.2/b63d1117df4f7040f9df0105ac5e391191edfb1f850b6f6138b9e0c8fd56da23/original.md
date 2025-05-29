A dictionary containing brief descriptions of each `Process` field:.

  * `process`: A `Function` with a method for `Process` types that performs a particular simulation. See [NonstationaryProcesses.jl](https://github.com/brendanjohnharris/NonstationaryProcesses.jl) for examples.
  * `parameter_profile`: A tuple of `Function`s that describe how each parameter of a system evolves over time. These can be functions, or curried functions of parameters given in `:parameter_profile_parameters`. See e.g. [`constantParameter`](@ref ParameterProfiles.constantParameter), [`Discontinuous`](@ref)
  * `parameter_profile_parameters`: A tuple of parameters (which may also be tuples) for each `:parameter_profile`
  * `X0`: The initial conditions, given as a vector equal in length to number of variables in the system
  * `t0`: The initial time of the simulation, at which the system has the state `:X0`
  * `transient_t0`: The length of time to simulate the system, from the initial conditions `:X0` at `:t0`, that is discarded when retrieving the [`timeseries`](@ref)
  * `dt`: The time step of the simulation and solver
  * `savedt`: The sampling period of the solution's [`timeseries`](@ref), which must be a multiple of `:dt`
  * `tmax`: The final time point of the simulation. The duration of the simulation is then `:tmax - :transient_t0`, and the duration of the returned time series is `:tmax - :t0`. See [`times`](@ref)
  * `alg`: The algorithm used to solve `DifferentialEquations.jl` processes. See, for example, a list of [ODE solvers](https://diffeq.sciml.ai/stable/solvers/ode_solve/)
  * `solver_opts`: A dictionary of additional options passed to the `:alg`. This can include solver tolerances, adaptive timesteps, or the maximum number of iterations. See the [common solver options](https://diffeq.sciml.ai/stable/basics/common_solver_opts/)
  * `solver_rng`: An integer seed for the random number generator, set to a random number by default
  * `id`: A unique integer ID for a given [`Process`](@ref)
  * `date`: The date at which the [`Process`](@ref) was created
  * `solution`: The solution of the simulation in its native format (e.g. an [ODE solution](https://diffeq.sciml.ai/stable/types/ode_types/#SciMLBase.ODESolution))
  * `varnames`: Dummy names for the variables of a [`Process`](@ref), defaulting to `[:x, :y, :z, ...]`
