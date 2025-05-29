```
named_ss(sys::ExtendedStateSpace;       kwargs...)
named_ss(sys::ExtendedStateSpace, name; kwargs...)
```

Assign names to an ExtendedStateSpace. If no specific names are provided for signals `z,y,w,u` and states`x`, names will be generated automatically.

# Arguments:

  * `name`: Prefix to add to all automatically generated names.
  * `x`
  * `u`
  * `y`
  * `w`
  * `z`
