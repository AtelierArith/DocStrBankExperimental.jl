```
XPRSgetattribinfo(prob, name)::id, type
```

Accesses the id number and the type information of an attribute given its name.

An attribute name may be for example `XPRS_ROWS`. Names are case-insensitive and may or may not have the `XPRS_` prefix. The id number is the constant used to identify the attribute for calls to functions such as XPRSgetintattrib. The type information returned will be one of the below integer constants defined in the `xprs.h` header file. The function will return an id number of 0 and a type value of `XPRS_TYPE_NOTDEFINED` if the name is not recognized as an attribute name. Note that this will occur if the name is a control name and not an attribute name.

# Arguments

  * `prob::XPRSprob`: The current problem.
  * `name::Union{Nothing,AbstractString}`: The name of the attribute to be queried.

# Return values

  * `id::Int32`: Pointer to an integer where the id number will be returned.
  * `type::XPRSParameterType`: Pointer to an integer where the type id will be returned.

See also the documentation of the correponding function [XPRSgetattribinfo](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSgetattribinfo.html) in the C API.
