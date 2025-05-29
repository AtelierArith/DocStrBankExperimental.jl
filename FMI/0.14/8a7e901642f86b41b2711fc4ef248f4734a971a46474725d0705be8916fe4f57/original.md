```
simulateME(fmu, instance=nothing, tspan=nothing; kwargs...)
simulateME(fmu, tspan; kwargs...)
simulateME(instance, tspan; kwargs...)
```

Simulate ME-FMU for the given simulation time interval. State- and Time-Events are handled correctly.

# Arguments

  * `fmu::FMU`: The FMU to be simulated.
  * `c::Union{FMUInstance, Nothing}=nothing`: The instance (FMI3) or component (FMI2) of the FMU, `nothing` if not available.
  * `tspan::Union{Tuple{Float64, Float64}, Nothing}=nothing`: Simulation-time-span as tuple (default = nothing: use default value from FMU's model description or (0.0, 1.0) if not specified)

# Keyword arguments

  * `solver = nothing`: Any Julia-supported ODE-solver (default = nothing: use DifferentialEquations.jl default solver)
  * `recordValues::fmi2ValueReferenceFormat` = nothing: Array of variables (Strings or variableIdentifiers) to record. Results are returned as `DiffEqCallbacks.SavedValues`
  * `recordEventIndicators::Union{AbstractArray{<:Integer, 1}, UnitRange{<:Integer}, Nothing} = nothing`: Array or Range of event indicators to record
  * `recordEigenvalues::Bool=false`: compute and record eigenvalues
  * `saveat = nothing`: Time points to save (interpolated) values at (default = nothing: save at each solver timestep)
  * `x0::Union{AbstractArray{<:Real}, Nothing} = nothing`: initial fmu State (default = nothing: use current or default-initial fmu state)
  * `setup::Bool`: call fmi2SetupExperiment, fmi2EnterInitializationMode and fmi2ExitInitializationMode before the simulation (default = nothing: use value from `fmu`'s `FMUExecutionConfiguration`)
  * `reset::Bool`: call fmi2Reset before each the simulation (default = nothing: use value from `fmu`'s `FMUExecutionConfiguration`)
  * `instantiate::Bool`: call fmi2Instantiate! simulate on a new created instance (default = nothing: use value from `fmu`'s `FMUExecutionConfiguration`)
  * `freeInstance::Bool`: call fmi2FreeInstance at the end of the simulation (default = nothing: use value from `fmu`'s `FMUExecutionConfiguration`)
  * `terminate::Bool`: call fmi2Terminate at the end of the simulation (default = nothing: use value from `fmu`'s `FMUExecutionConfiguration`)
  * `inputValueReferences::fmi2ValueReferenceFormat = nothing`: Input variables (Strings or variableIdentifiers) to set at each simulation step
  * `inputFunction = nothing`: Function to get values for the input variables at each simulation step.
  * `parameters::Union{Dict{<:Any, <:Any}, Nothing} = nothing`: Dict of parameter variables (strings or variableIdentifiers) and values (Real, Integer, Boolean, String) to set parameters during initialization
  * `callbacksBefore = []`: callbacks to call *before* the internal callbacks for state- and time-events are called
  * `callbacksAfter = []`: callbacks to call *after* the internal callbacks for state- and time-events are called
  * `showProgress::Bool = true`: print simulation progress meter in REPL
  * `solveKwargs...`: keyword arguments that get passed onto the solvers solve call

## Input function pattern

[`c`: current component, `u`: current state ,`t`: current time, returning array of values to be passed to `fmi2SetReal(..., inputValueReferences, inputFunction(...))` or `fmi3SetFloat64`]:

  * `inputFunction(t::Real, u::AbstractVector{<:Real})`
  * `inputFunction(c::Union{FMUInstance, Nothing}, t::Real, u::AbstractVector{<:Real})`
  * `inputFunction(c::Union{FMUInstance, Nothing}, x::AbstractVector{<:Real}, u::AbstractVector{<:Real})`
  * `inputFunction(x::AbstractVector{<:Real}, t::Real, u::AbstractVector{<:Real})`
  * `inputFunction(c::Union{FMUInstance, Nothing}, x::AbstractVector{<:Real}, t::Real, u::AbstractVector{<:Real})`

# Returns:

  * A [`FMUSolution`](@ref) struct.

See also [`simulate`](@ref), [`simulateCS`](@ref), [`simulateSE`](@ref).
