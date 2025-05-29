```
v_zero = reinit(instantiatedModel, _x, j, v_new, _leqMode; v_threshold=0.01)
```

Re-initialize state j with v*new, that is set x[i] = v*new, with i = instantiatedModel.equationInfo.x*info[j].startIndex. If v*new <= v*threshold, set x[i] to the floating point number that is closest to zero, so that x[i] > 0 and return v*zero = true. Otherwise return v_zero = false.

An error is triggered if the function is not called during an event phase or if leqMode >= 0 (which means that reinit is called inside the for-loop to solve a linear equation system - this is not yet supported).

# Implementation notes

At the beginning of getDerivatives!(..), assignments of *x to appropriate variables are performed. Therefore, setting _x[i] afterwards via reinit, has no immediate effect on this model evaluation. With reinit, instantiatedModel.eventHandler.newEventIteration = true is set, to force a new event iteration. At the next event iteration, the new value v*new is copied from _x and therefore has then an effect.
