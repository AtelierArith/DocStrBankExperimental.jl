```
mutable struct ExplicitLBDNParams{T, N, M}
```

Explicit LBDN parameter struct.

These parameters define the explicit form of a Lipschitz-bounded deep network used for model evaluation. Parameters are stored in `NTuple`s, where each element of an `NTuple` is the parameter for a single layer of the network. Tuples are faster to work with than vectors of arrays.

See [Wang et al. (2023)](https://proceedings.mlr.press/v202/wang23v.html) for more details on explicit parameterisations of LBDN.
