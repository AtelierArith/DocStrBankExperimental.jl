```
epgRotation!(E::EPGStates, alpha::Float64, phi::Float64=0.0)
```

applies Bloch-rotation (<=> RF pulse) to a set of EPG states.

# Arguments

  * `E::EPGStates``
  * `alpha::Float64`           - flip angle of the RF pulse (rad)
  * `phi::Float64=0.0`         - phase of the RF pulse (rad)
