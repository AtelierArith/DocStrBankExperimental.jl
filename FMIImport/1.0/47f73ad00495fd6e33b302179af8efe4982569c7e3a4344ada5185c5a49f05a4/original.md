```
fmi2DoStep(c::FMU2Component, 
                communicationStepSize::Union{Real, Nothing} = nothing; 
                currentCommunicationPoint::Union{Real, Nothing} = nothing,
                noSetFMUStatePriorToCurrentPoint::Bool = true)
```

Does one step in the CoSimulation FMU

# Arguments

  * `C::FMU2Component`: Mutable struct represents an instantiated instance of an FMU in the FMI 2.0.2 Standard.
  * `communicationStepSize::Union{Real, Nothing} = nothing`: Argument `communicationStepSize` contains a value of type `Real` or `Nothing` , if no argument is passed the default value `nothing` is used. `communicationStepSize` defines the communiction step size.

# Keywords

  * `currentCommunicationPoint::Union{Real, Nothing} = nothing`: Argument `currentCommunicationPoint` contains a value of type `Real` or type `Nothing`. If no argument is passed the default value `nothing` is used. `currentCommunicationPoint` defines the current communication point of the master.
  * `noSetFMUStatePriorToCurrentPoint::Bool = true`: Argument `noSetFMUStatePriorToCurrentPoint` contains a value of type `Boolean`. If no argument is passed the default value `true` is used. `noSetFMUStatePriorToCurrentPoint` indicates whether `fmi2SetFMUState` is no longer called for times before the `currentCommunicationPoint` in this simulation run Simulation run.

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
  * FMISpec2.0.2[p.104]: 4.2.2 Computation

See also [`fmi2DoStep`](@ref).
