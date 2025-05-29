```
scatteredfield(sphere::PECSphere, excitation::SphericalModeTE, point, quantity::ElectricField; parameter::Parameter=Parameter())
```

Compute the electric field scattered by a PEC sphere, when excited by a spherical mode travelling towards the origin.

The point and the returned field are in Cartesian coordinates.
