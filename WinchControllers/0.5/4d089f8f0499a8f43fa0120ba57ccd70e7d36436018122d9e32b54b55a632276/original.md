```
function get_state(m3::Mixer_3CH)
```

Return the controller state as integer.

Returns [WinchControllerState](@ref) as integer.

  * wcsLowerForceControl = 0 # input b selected
  * wcsSpeedControl = 1      # input a selected
  * wcsUpperForceControl = 2 # input c selected
