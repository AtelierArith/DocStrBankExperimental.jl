```
IndependentlyLinearizedSolution
```

Efficient datastructure that holds a set of independently linearized solutions (obtained via the `LinearizingSavingCallback`) with related, but slightly different time vectors.  Stores a single time vector with a packed `BitMatrix` denoting which `u` vectors are sampled at which timepoints.  Provides an efficient `iterate()` method that can be used to reconstruct coherent views of the state variables at all timepoints, as well as an efficient `sample!()` method that can sample at arbitrary timesteps.
