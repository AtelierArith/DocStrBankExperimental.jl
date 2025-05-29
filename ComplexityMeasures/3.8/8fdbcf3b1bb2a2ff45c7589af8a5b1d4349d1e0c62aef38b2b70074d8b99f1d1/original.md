```
transferoperator(pts::StateSpaceSet, binning; kw...)
```

Approximate the transfer operator given a set of sequentially ordered points subject to a rectangular partition given by the `binning`. The keywords `boundary_condition = :none, warn_precise = true` are as in [`TransferOperator`](@ref).
