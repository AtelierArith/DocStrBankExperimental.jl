```
detectvlinearity!(p::VRep, solver=default_solver(p); kws...)
```

Detects all the lines contained in the V-representation and remove all redundant lines.

The remaining keyword arguments `kws` are passed to [`detectvlinearity`](@ref).

## Examples

The representation

```julia
v = conichull([1, 1], [-1, -1])
```

contains the line `Line([1, 1])`.
