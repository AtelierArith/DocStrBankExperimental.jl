```
XPRSsetcheckedmode(checkedmode)::Nothing
```

You can use this function to disable some of the checking and validation of function calls and function call parameters for calls to the Xpress Optimizer API.

This checking is relatively lightweight but disabling it can improve performance in cases where non-intensive Xpress Optimizer functions are called repeatedly in a short space of time. Please note: after disabling function call checking and validation, invalid usage of Xpress Optimizer functions may not be detected and may cause the Xpress Optimizer process to behave unexpectedly or crash. It is not recommended that you disable function call checking and validation during application development.

# Arguments

  * `checkedmode::Integer`: Pass as 0 to disable much of the validation for all Xpress function calls from the current process.

See also the documentation of the correponding function [XPRSsetcheckedmode](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSsetcheckedmode.html) in the C API.
