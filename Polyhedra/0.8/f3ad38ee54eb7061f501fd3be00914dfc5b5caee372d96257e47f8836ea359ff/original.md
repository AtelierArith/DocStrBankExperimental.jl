```
allhalfspaces(hrep::HRep)
```

Returns an iterator over the halfspaces and hyperplanes in the H-representation `hrep` splitting hyperplanes in two halfspaces.

### Examples

```julia
hrep = HyperPlane([1, 0], 1) ∩ HalfSpace([0, 1], 1)
collect(allhalfspaces(hrep)) # Returns [HalfSpace([1, 0]), HalfSpace([-1, 0]), HalfSpace([0, 1])]
```
