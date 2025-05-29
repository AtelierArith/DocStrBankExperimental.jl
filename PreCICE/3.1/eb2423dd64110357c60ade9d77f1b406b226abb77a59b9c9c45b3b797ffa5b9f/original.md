```
isCouplingOngoing()::Bool
```

Check if the coupled simulation is still ongoing.

A coupling is ongoing as long as

  * the maximum number of timesteps has not been reached, and
  * the final time has not been reached.

The user should call [`finalize`](@ref) after this function returns false.

# Notes

Previous calls:

  * [`initialize`](@ref) has been called successfully.
