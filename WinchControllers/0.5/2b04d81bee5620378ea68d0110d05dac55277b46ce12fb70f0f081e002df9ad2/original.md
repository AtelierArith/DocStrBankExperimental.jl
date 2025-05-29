```
get_v_error(sc::SpeedController)
```

Compute and return the velocity error for the given `SpeedController` instance `sc`.

# Arguments

  * sc::[SpeedController](@ref): The speed controller object for which the velocity error is to be calculated.

# Returns

  * The velocity error `v_err` [m/s].  If the controller is inactive, it returns `0.0`.
