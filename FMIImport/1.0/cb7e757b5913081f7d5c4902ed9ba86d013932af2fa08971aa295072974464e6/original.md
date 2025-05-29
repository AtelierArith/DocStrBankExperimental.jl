```
fmi3SetUInt16(c::FMU3Instance, vr::AbstractArray{fmi3ValueReference}, nvr::Csize_t, value::AbstractArray{fmi3UInt16}, nvalue::Csize_t)
```

Functions to get and set values of variables idetified by their valueReference.

# Arguments

  * `c::FMU3Instance`: Argument `c` is a Mutable struct represents an instantiated instance of an FMU in the FMI 3.0 Standard.
  * `vr::AbstractArray{fmi3ValueReference}`: Argument `vr` is an AbstractArray of `nvr` value handels called "ValueReference" that define the variable that shall be inquired.
  * `nvr::Csize_t`: Argument `nvr` defines the size of `vr`.
  * `values::AbstractArray{fmi3UInt16}`: Argument `values` is an AbstractArray with the actual values of these variables.
  * `nvalue::Csize_t`: Argument `nvalue` defines the size of `values`.

# Returns

  * `status::fmi3Status`: Return `status` is an enumeration of type `fmi3Status` and indicates the success of the function call.

More detailed:     - `fmi3OK`: all well     - `fmi3Warning`: things are not quite right, but the computation can continue     - `fmi3Discard`: if the slave computed successfully only a subinterval of the communication step     - `fmi3Error`: the communication step could not be carried out at all     - `fmi3Fatal`: if an error occurred which corrupted the FMU irreparably

# Source

  * FMISpec3.0 Link: [https://fmi-standard.org/](https://fmi-standard.org/)
  * FMISpec3.0: 2.2.3 Platform Dependent Definitions
  * FMISpec3.0: 2.2.4 Status Returned by Functions
  * FMISpec3.0: 2.2.6.2. Getting and Setting Variable Values
