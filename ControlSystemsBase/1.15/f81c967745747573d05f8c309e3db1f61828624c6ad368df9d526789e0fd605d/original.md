```
minreal(sys::StateSpace; fast=false, balance=true, kwargs...)
```

Minimal realisation algorithm from P. Van Dooreen, The generalized eigenstructure problem in linear system theory, IEEE Transactions on Automatic Control

For information about the options, see `?ControlSystemsBase.MatrixPencils.lsminreal`

See also [`sminreal`](@ref), which is both numerically exact and substantially faster than `minreal`, but with a much more limited potential in removing non-minimal dynamics.
