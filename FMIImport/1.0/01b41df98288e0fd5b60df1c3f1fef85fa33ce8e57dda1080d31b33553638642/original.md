```
fmi2SetupExperiment(c::FMU2Component, toleranceDefined::fmi2Boolean, tolerance::fmi2Real, startTime::fmi2Real, stopTimeDefined::fmi2Boolean, stopTime::fmi2Real)
```

Informs the FMU to setup the experiment. This function must be called after `fmi2Instantiate` and before `fmi2EnterInitializationMode` is called.

# Arguments

  * `c::FMU2Component`: Argument `c` is a Mutable struct represents an instantiated instance of an FMU in the FMI 2.0.2 Standard.
  * `toleranceDefined::fmi2Boolean`: Arguments `toleranceDefined` depend on the FMU type:

      * fmuType = fmi2ModelExchange: If `toleranceDefined = fmi2True`, then the model is called with a numerical integration scheme where the step size is controlled by using `tolerance` for error estimation. In such a case, all numerical algorithms used inside the model (for example, to solve non-linear algebraic equations) should also operate with an error estimation of an appropriate smaller relative tolerance.
      * fmuType = fmi2CoSimulation: If `toleranceDefined = fmi2True`, then the communication interval of the slave is controlled by error estimation.  In case the slave utilizes a numerical integrator with variable step size and error estimation, it is suggested to use “tolerance” for the error estimation of the internal integrator (usually as relative tolerance). An FMU for Co-Simulation might ignore this argument.
  * `startTime::fmi2Real`: Argument `startTime` can be used to check whether the model is valid within the given boundaries or to allocate memory which is necessary for storing results. It is the fixed initial value of the independent variable and if the independent variable is `time`, `startTime` is the starting time of initializaton.
  * `stopTimeDefined::fmi2Boolean`:  If `stopTimeDefined = fmi2True`, then stopTime is the defined final value of the independent variable and if `stopTimeDefined = fmi2False`, then no final value

of the independent variable is defined and argument `stopTime` is meaningless.

  * `stopTime::fmi2Real`: Argument `stopTime` can be used to check whether the model is valid within the given boundaries or to allocate memory which is necessary for storing results. It is the fixed final value of the independent variable and if the independent variable is “time”, stopTime is the stop time of the simulation.

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
  * FMISpec2.0.2[p.22]: 2.1.2 Platform Dependent Definitions (fmi2TypesPlatform.h)
  * FMISpec2.0.2[p.22]: 2.1.3 Status Returned by Functions
  * FMISpec2.0.2[p.22]: 2.1.6 Initialization, Termination, and Resetting an FMU

See also [`fmi2SetupExperiment`](@ref).
