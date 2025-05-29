```
get_state(wc::WinchController) -> @enum WinchControllerState
```

Returns the current state of the given `WinchController` instance `wc`. The returned value typically represents the operational state or status of the winch controller, such as position, speed, or error status.

# Arguments

  * `wc::WinchController`: The winch controller object whose state is to be retrieved.

# Returns

  * @enum [WinchControllerState](@ref)
