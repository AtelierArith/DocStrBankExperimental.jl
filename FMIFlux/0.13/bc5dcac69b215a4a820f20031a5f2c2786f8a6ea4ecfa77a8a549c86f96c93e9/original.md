DEPRECATED:

Performs something similar to `fmiDoStep` for ME-FMUs (note, that fmiDoStep is for CS-FMUs only). Event handling (state- and time-events) is supported. If you don't want events to be handled, you can disable event-handling for the NeuralFMU `nfmu` with the attribute `eventHandling = false`.

Optional, additional FMU-values can be set via keyword arguments `setValueReferences` and `setValues`. Optional, additional FMU-values can be retrieved by keyword argument `getValueReferences`.

Function takes the current system state array ("x") and returns an array with state derivatives ("x dot") and optionally the FMU-values for `getValueReferences`. Setting the FMU time via argument `t` is optional, if not set, the current time of the ODE solver around the NeuralFMU is used.
