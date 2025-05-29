```
fmi3GetShiftFraction!(c::FMU3Instance, vr::AbstractArray{fmi3ValueReference}, nvr::Csize_t, shiftCounters::AbstractArray{fmi3UInt64}, resolutions::AbstractArray{fmi3UInt64})
```

fmi3GetShiftFraction retrieves the delay to the first Clock tick from the FMU.

# TODO argmuents

# Arguments

  * `c::FMU3Instance`: Argument `c` is a Mutable struct represents an instantiated instance of an FMU in the FMI 3.0 Standard.
  * `vr::AbstractArray{fmi3ValueReference}`: Argument `vr` is an AbstractArray of `nvr` value handels called "ValueReference" that define the variable that shall be inquired.
  * `nvr::Csize_t`: Argument `nvr` defines the size of `vr`.
  * `shiftCounters::AbstractArray{fmi3UInt64}`:
  * `resolutions::AbstractArray{fmi3UInt64}`:

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
  * FMISpec3.0: 2.2.9. Clocks

See also [`fmi3GetShiftFraction!`](@ref).
