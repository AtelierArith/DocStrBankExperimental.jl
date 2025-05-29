```
eigfunc_expansion(z, params::NamedTuple; period=2π, nb_terms=50)
```

Compute the α-quasi-periodic Green's function using the eigenfunction expansion.

# Input arguments

  * z: coordinates of the difference between the target point and source point.
  * params: named tuple of the physical and numerical parameters for the problem definition.

# Returns

  * The value of the α-quasi-periodic Green's function for 2D Helmholtz equation at the point z, computed by the basic eigenfunction expansion.
