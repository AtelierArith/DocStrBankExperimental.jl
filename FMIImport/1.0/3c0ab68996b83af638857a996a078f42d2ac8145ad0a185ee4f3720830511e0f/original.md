```
fmi3InstantiateScheduledExecution!(fmu::FMU3; ptrlockPreemption::Ptr{Cvoid}, ptrunlockPreemption::Ptr{Cvoid}, instanceName::String=fmu.modelName, type::fmi3Type=fmu.type, pushInstances::Bool = true, visible::Bool = false, loggingOn::Bool = fmu.executionConfig.loggingOn, externalCallbacks::Bool = fmu.executionConfig.externalCallbacks, 
    logStatusOK::Bool=true, logStatusWarning::Bool=true, logStatusDiscard::Bool=true, logStatusError::Bool=true, logStatusFatal::Bool=true)
```

Create a new ScheduledExecution instance of the given fmu, adds a logger if `logginOn == true`.

# Arguments

  * `fmu::FMU3`: Mutable struct representing a FMU and all it instantiated instances in the FMI 3.0 Standard.

# Keywords

  * `ptrlockPreemption::Ptr{Cvoid}`: Points to a function handling locking Preemption
  * `ptrunlockPreemption::Ptr{Cvoid}`: Points to a function handling unlocking Preemption
  * `instanceName::String=fmu.modelName`: Name of the instance
  * `type::fmi3Type=fmu.type`: Defines whether a Co-Simulation or Model Exchange is present
  * `pushInstances::Bool = true`: Defines if the fmu instances should be pushed in the application.
  * `visible::Bool = false` if the FMU should be started with graphic interface, if supported (default=`false`)
  * `loggingOn::Bool = fmu.executionConfig.loggingOn` if the FMU should log and display function calls (default=`false`)
  * `externalCallbacks::Bool = fmu.executionConfig.externalCallbacks` if an external shared library should be used for the fmi3CallbackFunctions, this may improve readability of logging messages (default=`false`)
  * `logStatusOK::Bool=true` whether to log status of kind `fmi3OK` (default=`true`)
  * `logStatusWarning::Bool=true` whether to log status of kind `fmi3Warning` (default=`true`)
  * `logStatusDiscard::Bool=true` whether to log status of kind `fmi3Discard` (default=`true`)
  * `logStatusError::Bool=true` whether to log status of kind `fmi3Error` (default=`true`)
  * `logStatusFatal::Bool=true` whether to log status of kind `fmi3Fatal` (default=`true`)

# Returns

  * Returns the instance of a new FMU ScheduledExecution instance.

# Source

  * FMISpec3.0 Link: [https://fmi-standard.org/](https://fmi-standard.org/)
  * FMISpec3.0: 2.4.7  Model variables
  * FMISpec3.0: 2.3.1. Super State: FMU State Setable

See also [`fmi3InstantiateScheduledExecution`](#@ref).
