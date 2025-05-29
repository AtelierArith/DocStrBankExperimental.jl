```
propagate!(state[s], model::HiddenStateModel[, dt])
```

Propagates the state(s) according to the model. For `ContinuousTime' models, a time step`dt' has to be provided. Multiple states are given as a matrix with columns corresponding to states, and are processed i.i.d.
