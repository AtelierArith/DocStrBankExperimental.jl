```
image_expansion_smooth(z, params::NamedTuple; period=2π, nb_terms=50)
```

Compute the smooth α-quasi-periodic Green's function (i.e. without the term $H_0^{(1)(k|x|)}$ using the image expansion.

# Input arguments

  * z: coordinates of the difference between the target point and source point.
  * params: named tuple of the physical and numerical parameters for the problem definition.

# Returns

  * The value of the smooth α-quasi-periodic Green's function for the 2D Helmholtz equation at the point z, computed via the basic image expansion.
