```
CrystalNet{D,T<:Real}
```

Representation of a net as a topological abstraction of a crystal.

`D` is the dimensionality of the net, which is the number of repeated dimensions of a single connex component. This dimensionality is not necessarily the dimension of the space the crystal is embedded into, which would always be 3 for real space.

`T` is the numeric type used to store the exact coordinates of each vertex at the equilibrium placement.
