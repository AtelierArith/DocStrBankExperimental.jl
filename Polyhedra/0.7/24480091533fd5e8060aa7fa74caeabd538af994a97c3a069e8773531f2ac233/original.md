```
detecthlinearity!(p::HRep; kws...)
```

Detects all the hyperplanes contained in the H-representation and remove all redundant hyperplanes.

The remaining keyword arguments `kws` are passed to [`detecthlinearity`](@ref).

## Examples

The representation

```julia
h = HalfSpace([1, 1], 1]) ∩ HalfSpace([-1, -1], -1)
```

contains the hyperplane `HyperPlane([1, 1], 1)`.
