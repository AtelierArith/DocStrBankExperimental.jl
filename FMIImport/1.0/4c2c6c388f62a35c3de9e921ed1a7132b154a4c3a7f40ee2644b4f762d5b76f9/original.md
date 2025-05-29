```
fmi2Instantiate!(fmu::FMU2;
                    instanceName::String=fmu.modelName,
                    type::fmi2Type=fmu.type,
                    pushComponents::Bool = true,
                    visible::Bool = false,
                    loggingOn::Bool = fmu.executionConfig.loggingOn,
                    externalCallbacks::Bool = fmu.executionConfig.externalCallbacks,
                    logStatusOK::Bool=true,
                    logStatusWarning::Bool=true,
                    logStatusDiscard::Bool=true,
                    logStatusError::Bool=true,
                    logStatusFatal::Bool=true,
                    logStatusPending::Bool=true)
```

Create a new instance of the given fmu, adds a logger if logginOn == true.

# Arguments

  * `fmu::FMU2`: Mutable struct representing a FMU and all it instantiated instances in the FMI 2.0.2 Standard.

# Keywords

  * `instanceName::String=fmu.modelName`: Name of the instance
  * `type::fmi2Type=fmu.type`: Defines whether a Co-Simulation or Model Exchange is present
  * `pushComponents::Bool = true`: Defines if the fmu components should be pushed in the application.
  * `visible::Bool = false` if the FMU should be started with graphic interface, if supported (default=`false`)
  * `loggingOn::Bool = fmu.executionConfig.loggingOn` if the FMU should log and display function calls (default=`false`)
  * `externalCallbacks::Bool = fmu.executionConfig.externalCallbacks` if an external shared library should be used for the fmi2CallbackFunctions, this may improve readability of logging messages (default=`false`)
  * `logStatusOK::Bool=true` whether to log status of kind `fmi2OK` (default=`true`)
  * `logStatusWarning::Bool=true` whether to log status of kind `fmi2Warning` (default=`true`)
  * `logStatusDiscard::Bool=true` whether to log status of kind `fmi2Discard` (default=`true`)
  * `logStatusError::Bool=true` whether to log status of kind `fmi2Error` (default=`true`)
  * `logStatusFatal::Bool=true` whether to log status of kind `fmi2Fatal` (default=`true`)
  * `logStatusPending::Bool=true` whether to log status of kind `fmi2Pending` (default=`true`)

# Returns

  * Returns the instance of a new FMU component.

# Source

  * FMISpec2.0.2 Link: [https://fmi-standard.org/](https://fmi-standard.org/)
  * FMISpec2.0.2: 2.2.7  Definition of Model Variables (ModelVariables)

See also [`fmi2Instantiate`](#@ref).
