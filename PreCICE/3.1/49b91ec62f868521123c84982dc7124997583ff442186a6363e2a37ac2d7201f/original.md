```
finalize()
```

Finalize the coupling to the coupling supervisor.

If initialize() has been called:

  * synchronizes with remote participants
  * handles final exports
  * cleans up general state
  * closes communication channels

Always:

  * flushes and finalizes Events
  * finalizes managed PETSc
  * finalizes managed MPI
