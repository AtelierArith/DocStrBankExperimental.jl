```
EveryStepCallback(affect, finalize)
```

A generic callback that calls the function `affect` on the simulation state in every [`prepropagate!`](@ref) hook. Calls `finalize` on successfull termination of the simulation (see [`finalize!`](@ref)).
