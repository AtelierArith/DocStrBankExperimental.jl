```
image_expansion_derivative(z, params::NamedTuple; period=2π, nb_terms=50)
```

Compute the derivative of the α-quasi-periodic Green's function using the image expansion.

# Input arguments

  * z: coordinates of the difference between the target point and source point.
  * params: named tuple of the physical and numerical parameters for the problem definition.

# Returns

  * The value of the derivative of the α-quasi-periodic Green's function for the 2D Helmholtz equation at the point z, computed via the basic image expansion.
