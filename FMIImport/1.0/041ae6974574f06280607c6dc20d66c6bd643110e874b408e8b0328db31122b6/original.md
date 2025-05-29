```
fmi2SetupExperiment(c::FMU2Component, 
                        startTime::Union{Real, Nothing} = nothing, 
                        stopTime::Union{Real, Nothing} = nothing; 
                        tolerance::Union{Real, Nothing} = nothing)
```

Setup the simulation but without defining all of the parameters.

# Arguments

  * `c::fmi2Struct`:  Representative for an FMU in the FMI 2.0.2 Standard.

More detailed: `fmi2Struct = Union{FMU2, FMU2Component}`

  * `c::FMU2`: Mutable struct representing a FMU and all it instantiated instances in the FMI 2.0.2 Standard.
  * `c::FMU2Component`: Mutable struct representing an instantiated instance of an FMU in the FMI 2.0.2 Standard.
  * `startTime::Union{Real, Nothing} = nothing`: `startTime` is a real number which sets the value of starting time of the experiment. The default value is set automatically if doing nothing (default = `nothing`).
  * `stopTime::Union{Real, Nothing} = nothing`: `stopTime` is a real number which sets the value of ending time of the experiment. The default value is set automatically if doing nothing (default = `nothing`).

# Keywords

  * `tolerance::Union{Real, Nothing} = nothing`: `tolerance` is a real number which sets the value of tolerance range. The default value is set automatically if doing nothing (default = `nothing`).

# Returns

  * Returns a warning if `str.state` is not called in `fmi2ComponentStateInstantiated`.
  * `status::fmi2Status`: Return `status` is an enumeration of type `fmi2Status` and indicates the success of the function call.

More detailed:

  * `fmi2OK`: all well
  * `fmi2Warning`: things are not quite right, but the computation can continue
  * `fmi2Discard`: if the slave computed successfully only a subinterval of the communication step
  * `fmi2Error`: the communication step could not be carried out at all
  * `fmi2Fatal`: if an error occurred which corrupted the FMU irreparably
  * `fmi2Pending`: this status is returned if the slave executes the function asynchronously

# Source

  * FMISpec2.0.2 Link: [https://fmi-standard.org/](https://fmi-standard.org/)
  * FMISpec2.0.2[p.23]: 2.1.6 Initialization, Termination, and Resetting an FMU
  * FMISpec2.0.2[p.18]: 2.1.3 Status Returned by Functions

See also [`fmi2SetupExperiment`](@ref).
