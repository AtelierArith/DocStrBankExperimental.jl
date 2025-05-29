```
TransitTiming(tmax, ic; ti)
```

Constructor for [`TransitTiming`](@ref) type.

# Arguments

  * `tmax::T` : Expected total elapsed integration time. (Allocates arrays accordingly)
  * `ic::ElementsIC{T}` : Initial conditions for the system

## Optional

  * `ti::Int64=1` : Index of the body with respect to which transits are measured. (Default is the central body)
