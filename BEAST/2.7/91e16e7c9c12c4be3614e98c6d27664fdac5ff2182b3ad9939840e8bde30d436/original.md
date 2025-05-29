```
marchonintime(W0,Z,B,I; convhist=false)
```

Solve by marching-on-in-time the causal convolution problem defined by `(W0,Z,B)` up to timestep `I`. Here, `Z` is an array of order 3 that contains a discretisation of a time translation invariant retarded potential operator. `W0` is the inverse of the slice `Z[:,:,1]`.

Keyword arguments:     - 'convhist': when true, return in addition to the space-time data for the     solution also the vector of convergence histories as returned each time step     by the supplied solver `W0`.
