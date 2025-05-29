```
currenttimestep(simdata::AbstractSimData)
```

Retrieve the current timestep from a [`AbstractSimData`](@ref) object.

This may be different from the `timestep`. If the timestep is `Month`, `currenttimestep` will return `Seconds` for the length of the specific month.
