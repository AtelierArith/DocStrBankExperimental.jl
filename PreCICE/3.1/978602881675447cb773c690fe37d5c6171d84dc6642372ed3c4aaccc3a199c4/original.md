```
isTimeWindowComplete()::Bool
```

Check if the current coupling timewindow is completed.

The following reasons require several solver time steps per coupling time step:

  * A solver chooses to perform subcycling.
  * An implicit coupling timestep iteration is not yet converged.

# Notes

Previous calls:

  * [`initialize`](@ref) has been called successfully.
