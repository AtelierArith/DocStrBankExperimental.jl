```
scatteredfield(sphere::PECSphere, excitation::FitzgeraldDipole, quantity::FarField; parameter::Parameter=Parameter())
```

Compute the electric far-field scattered by a PEC sphere, where the dipole is placed along the z-axis at z0.

The point and the returned field are in Cartesian coordinates.
