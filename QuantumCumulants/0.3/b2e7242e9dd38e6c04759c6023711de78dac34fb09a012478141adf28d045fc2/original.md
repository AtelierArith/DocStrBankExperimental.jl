```
acts_on(op)
```

Shows on which Hilbert space `op` acts. For [`QSym`](@ref) types, this returns an Integer, whereas for a `Term` it returns a `Vector{Int}` whose entries specify all subspaces on which the expression acts.
