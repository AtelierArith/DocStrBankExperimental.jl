```
potentialoperator([T=Float64,] b::CompositeBasis, V(x, y, z, ...))
```

Operator representing a potential $V$ in more than one dimension.

# Arguments

  * `b`: Composite basis consisting purely either of `PositionBasis` or   `MomentumBasis`. Note, that calling this with a composite basis in   momentum space might consume a large amount of memory.
  * `V`: Function describing the potential. ATTENTION: The number of arguments   accepted by `V` must match the spatial dimension. Furthermore, the order   of the arguments has to match that of the order of the tensor product of   bases (e.g. if `b=bx⊗by⊗bz`, then `V(x,y,z)`).
