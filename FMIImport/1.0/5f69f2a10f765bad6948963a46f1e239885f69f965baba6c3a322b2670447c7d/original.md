```
fmi2SetTime(c::FMU2Component, 
                time::fmi2Real; 
                soft::Bool=false,
                track::Bool=true,
                force::Bool=c.fmu.executionConfig.force,
                time_shift::Bool=c.fmu.executionConfig.autoTimeShift)
```

Set a new time instant and re-initialize caching of variables that depend on time, provided the newly provided time value is different to the previously set time value (variables that depend solely on constants or parameters need not to be newly computed in the sequel, but the previously computed values can be reused).

# Arguments

  * `c::FMU2Component`: Mutable struct represents an instantiated instance of an FMU in the FMI 2.0.2 Standard.
  * `time::fmi2Real`: Argument `time` contains a value of type `fmi2Real` which is a alias type for `Real` data type. `time` sets the independent variable time t.

# Keywords

  * `soft::Bool=false`: If the Keyword `soft = true` the command is only performed if the FMU is in an allowed state for this command.

-`track::Bool=true`: If the Keyword `track = true`

  * `time_shift::Bool=c.fmu.executionConfig.autoTimeShift`:

# Returns

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
  * FMISpec2.0.2[p.16]: 2.1.2 Platform Dependent Definitions (fmi2TypesPlatform.h)
  * FMISpec2.0.2[p.16]: 2.1.3 Status Returned by Functions
  * FMISpec2.0.2[p.83]: 3.2.1 Providing Independent Variables and Re-initialization of Caching

See also [`fmi2SetTime`](@ref).
