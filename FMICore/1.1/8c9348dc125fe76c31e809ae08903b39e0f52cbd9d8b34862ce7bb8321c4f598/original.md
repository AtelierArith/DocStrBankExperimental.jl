Defines the status flag (an enumeration of type fmi3Status defined in file fmi3FunctionTypes.h) that is returned by functions to indicate the success of the function call: The status has the following meaning:

  * fmi3OK: The call was successful. The output argument values are defined.
  * fmi3Warning: A non-critical problem was detected, but the computation can continue. The output argument values are defined. Function logMessage should be called by the FMU with further information before returning this status, respecting the current logging settings.

[In certain applications, e.g. in a prototyping environment, warnings may be acceptable. For production environments warnings should be treated like errors unless they can be safely ignored.]

  * fmi3Discard: The call was not successful and the FMU is in the same state as before the call. The output argument values are not defined, but the computation can continue. Function logMessage should be called by the FMU with further information before returning this status, respecting the current logging settings. Advanced simulation algorithms can try alternative approaches to drive the simulation by calling the function with different arguments or calling another function. Otherwise the simulation algorithm has to treat this return code like fmi3Error and has to terminate the simulation.

[Examples for usage of fmi3Discard are handling of min/max violation, or signal numerical problems during model evaluation forcing smaller step sizes.]

  * fmi3Error: The call failed. The output argument values are undefined and the simulation cannot be continued. Function logMessage should be called by the FMU with further information before returning this status, respecting the current logging settings. If a function returns fmi3Error, it is possible to restore a previously retrieved FMU state by calling fmi3SetFMUState. Otherwise fmi3FreeInstance or fmi3Reset must be called. When detecting illegal arguments or a function call not allowed in the current state according to the respective state machine, the FMU must return fmi3Error. Other instances of this FMU are not affected by the error.
  * fmi3Fatal: The state of all instances of the model is irreparably corrupted. [For example, due to a runtime exception such as access violation or integer division by zero during the execution of an FMI function.] Function logMessage should be called by the FMU with further information before returning this status, respecting the current logging settings, if still possible. It is not allowed to call any other function for any instance of the FMU.

Source: FMISpec3.0, Version D5ef1c1: 2.2.3. Status Returned by Functions
