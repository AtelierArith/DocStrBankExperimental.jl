```
refresh_med!(model)
```

Refresh the model evaluation data stored within the given model instance. Most notably, this is necessary when the steady state is used in the dynamic equations.

Normally there's no need for the end-used to call this function. It should be called when necessay by the solver.
