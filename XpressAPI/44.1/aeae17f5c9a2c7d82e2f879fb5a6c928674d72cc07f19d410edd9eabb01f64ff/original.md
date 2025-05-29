```
XPRSgetcontrolinfo(prob, name)::id, type
```

Accesses the id number and the type information of a control given its name.

A control name may be for example `XPRS_PRESOLVE`. Names are case-insensitive and may or may not have the `XPRS_` prefix. The id number is the constant used to identify the control for calls to functions such as XPRSgetintcontrol. The function will return an id number of `0` and a type value of `XPRS_TYPE_NOTDEFINED` if the name is not recognized as a control name. Note that this will occur if the name is an attribute name and not a control name.

# Arguments

  * `prob::XPRSprob`: The current problem.
  * `name::Union{Nothing,AbstractString}`: The name of the control to be queried.

# Return values

  * `id::Int32`: Pointer to an integer where the id number will be returned.
  * `type::XPRSParameterType`: Pointer to an integer where the type information will be returned.

See also the documentation of the correponding function [XPRSgetcontrolinfo](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSgetcontrolinfo.html) in the C API.
