```
TimedCallback(affect, executiontimes; offset=0.0, initialize, finalize)
```

A generic callback that calls the function `affect` on the simulation state in a [`prepropagate!`](@ref) hook whenever the simulation time is larger than one of the points specified in `executiontimes`. `executiontimes` must be indexable and sorted in ascending order (multiple identical  elements are fine).  The kwarg `offset` optionally shifts all execution times by the specified amount,  `initialize` and `finalize` functions are called when the callback is first executed   and on successfull termination of the simulation respectively.
