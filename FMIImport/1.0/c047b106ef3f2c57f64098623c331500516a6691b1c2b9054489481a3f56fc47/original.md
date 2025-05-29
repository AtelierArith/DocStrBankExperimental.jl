```
fmi2NewDiscreteStates!(c::FMU2Component, eventInfo::fmi2EventInfo)
```

The FMU is in Event Mode and the super dense time is incremented by this call.

# Arguments

  * `c::FMU2Component`: Mutable struct represents an instantiated instance of an FMU in the FMI 2.0.2 Standard.
  * `eventInfo::fmi2EventInfo*`: Strut with `fmi2Boolean` Variables that

More detailed:

  * `newDiscreteStatesNeeded::fmi2Boolean`: If `newDiscreteStatesNeeded = fmi2True` the FMU should stay in Event Mode, and the FMU requires to set new inputs to the FMU to compute and get the outputs and to call

fmi2NewDiscreteStates again. If all FMUs return `newDiscreteStatesNeeded = fmi2False` call fmi2EnterContinuousTimeMode.

  * `terminateSimulation::fmi2Boolean`: If `terminateSimulation = fmi2True` call `fmi2Terminate`
  * `nominalsOfContinuousStatesChanged::fmi2Boolean`: If `nominalsOfContinuousStatesChanged = fmi2True` then the nominal values of the states have changed due to the function call and can be inquired with `fmi2GetNominalsOfContinuousStates`.
  * `valuesOfContinuousStatesChanged::fmi2Boolean`: If `valuesOfContinuousStatesChanged = fmi2True`, then at least one element of the continuous state vector has changed its value due to the function call. The new values of the states can be retrieved with `fmi2GetContinuousStates`. If no element of the continuous state vector has changed its value, `valuesOfContinuousStatesChanged` must return fmi2False.
  * `nextEventTimeDefined::fmi2Boolean`: If `nextEventTimeDefined = fmi2True`, then the simulation shall integrate at most until `time = nextEventTime`, and shall call `fmi2EnterEventMode` at this time instant. If integration is stopped before nextEventTime, the definition of `nextEventTime` becomes obsolete.
  * `nextEventTime::fmi2Real`: next event if `nextEventTimeDefined=fmi2True`

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
  * FMISpec2.0.2[p.83]: 3.2.2 Evaluation of Model Equations

See also [`fmi2NewDiscreteStates`](@ref).
