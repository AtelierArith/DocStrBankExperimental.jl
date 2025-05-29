```
get_status(wc::WinchController)
```

Retrieve the current status of the given `WinchController` instance for logging and debugging purposes.

# Arguments

  * `wc::WinchController`: The winch controller object whose status is to be retrieved.

# Returns

  * The current status of the winch controller, an array containing:

      * `reset`: Boolean indicating if the controller is in reset state.
      * `active`: Boolean indicating if the controller is active.
      * `force`: The current set force value or zero if not set.
      * `f_set`: The set force value.
      * `v_set_out`: The output velocity set by the speed controller.
      * `v_set_ufc`: The output velocity set by the upper force controller.
      * `v_set_lfc`: The output velocity set by the lower force controller.
