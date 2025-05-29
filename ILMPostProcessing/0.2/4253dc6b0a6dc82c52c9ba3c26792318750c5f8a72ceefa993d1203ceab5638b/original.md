```
pod(X::Vector{T}[; tolerance=0.99])
```

Calculate the POD modes and associated time-varying coefficients from an array of snapshot data `X`. This `X` plays the role of a snapshot matrix, whose columns are snapshots of the data. However, it is actually to be stored as a type `Vector{T}` where `T<:GridData`. It can be generated with a function like `velocity(sol,sys,trange)`, where `sol` is a `ODESolution`, `sys` is an `ILMSystem`, and `trange` is an array of times, e.g., `trange=range(1,10,length=100)`. The number of POD modes retained in the decomposition is set by `tolerance`: this specifies the fraction of the total energy to keep, and defaults to 99 percent. 

The output of `PODModes` is a structure with the following fields

  * `Xmean`: temporal mean of the data. type `T`
  * `Xnorm`: original `X` vector with mean removed. Each element is of type `T`
  * `phi`: vector of POD modes. Each element is of type `T`
  * `a`: matrix of POD coefficients. Number of columns is same as number of entries in `phi`. Column `k` constitutes the time-varying coefficient for mode `k` in `phi`.
  * `lambda`: vector of modal energies, arranged in decreasing order, corresponding to the modes in `phi`
  * `psi`: matrix of
