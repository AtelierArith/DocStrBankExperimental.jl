```
fmi3UpdateDiscreteStates(c::FMU3Instance)
```

This function is called to signal a converged solution at the current super-dense time instant. fmi3UpdateDiscreteStates must be called at least once per super-dense time instant. Results are returned, use `fmi3UpdateDiscreteStates!` for the inplace variant.

# Arguments

  * `c::FMU3Instance`: Mutable struct represents an instantiated instance of an FMU in the FMI 3.0 Standard.

# Returns

  * `discreteStatesNeedUpdate`
  * `terminateSimulation`
  * `nominalsOfContinuousStatesChanged`
  * `valuesOfContinuousStatesChanged`
  * `nextEventTimeDefined`
  * `nextEventTime`

# Source

  * FMISpec3.0 Link: [https://fmi-standard.org/](https://fmi-standard.org/)
  * FMISpec3.0: 2.2.3 Platform Dependent Definitions
  * FMISpec3.0: 2.3.5. State: Event Mode
