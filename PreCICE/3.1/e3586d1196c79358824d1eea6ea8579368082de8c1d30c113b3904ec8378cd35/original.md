```
initialize()
```

Fully initializes preCICE and coupling data.

This function does the following:

  * Sets up a connection to the other participants of the coupled simulation.
  * Creates all meshes, solver meshes need to be submitted before.
  * Receives first coupling data. The starting values for coupling data are zero by default.
  * Determines maximum allowed size of the first time step to be computed.

# Notes

See also:

  * [`getMaxTimeStepSize`](@ref)
