```
fmi3SetDebugLogging(c::FMU3Instance, logginOn::fmi3Boolean, nCategories::UInt, categories::Ptr{Nothing})
```

Control the use of the logging callback function, version independent.

# Arguments

  * `c::FMU3Instance`: Argument `c` is a Mutable struct represents an instantiated instance of an FMU in the FMI 3.0 Standard.
  * `logginOn::fmi3Boolean`: If `loggingOn = fmi3True`, debug logging is enabled for the log categories specified in categories, otherwise it is disabled. Type `fmi3Boolean` is defined as an alias Type for the C-Type Boolean and is to be used with `fmi3True` and `fmi3False`.
  * `nCategories::UInt`: Argument `nCategories` defines the length of the argument `categories`.
  * `categories::Ptr{Nothing}`:

# Returns

  * `status::fmi3Status`: Return `status` is an enumeration of type `fmi3Status` and indicates the success of the function call.

More detailed:

  * `fmi3OK`: all well
  * `fmi3Warning`: things are not quite right, but the computation can continue
  * `fmi3Discard`: if the slave computed successfully only a subinterval of the communication step
  * `fmi3Error`: the communication step could not be carried out at all
  * `fmi3Fatal`: if an error occurred which corrupted the FMU irreparably

# Source

  * FMISpec3.0 Link: [https://fmi-standard.org/](https://fmi-standard.org/)
  * FMISpec3.0: 2.2.3 Platform Dependent Definitions
  * FMISpec3.0: 2.2.4 Status Returned by Functions
  * FMISpec3.0: 2.3.1. Super State: FMU State Setable

See also [`fmi3SetDebugLogging`](@ref).
