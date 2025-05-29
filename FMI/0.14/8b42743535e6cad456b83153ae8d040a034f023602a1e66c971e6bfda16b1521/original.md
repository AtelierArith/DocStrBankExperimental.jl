```
simulateSE(fmu, instance=nothing, tspan=nothing; kwargs...)
simulateSE(fmu, tspan; kwargs...)
simulateSE(instance, tspan; kwargs...)
```

To be implemented ...

# Arguments

  * `fmu::FMU3`: The FMU to be simulated. Note: SE is only available in FMI3.
  * `c::Union{FMU3Instance, Nothing}=nothing`: The instance (FMI3) of the FMU, `nothing` if not available.
  * `tspan::Union{Tuple{Float64, Float64}, Nothing}=nothing`: Simulation-time-span as tuple (default = nothing: use default value from FMU's model description or (0.0, 1.0) if not specified)

# Keyword arguments

  * To be implemented ...

# Returns:

  * A [`FMUSolution`](@ref) struct.

See also [`simulate`](@ref), [`simulateME`](@ref), [`simulateCS`](@ref).
