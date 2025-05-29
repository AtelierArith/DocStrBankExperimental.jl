```
scatteredfield(sphere::Sphere, excitation::PlaneWave, point, quantity::Field; parameter::Parameter=Parameter())
```

Compute the electric field scattered by a PEC or dielectric sphere, for an incident plane wave travelling in +z-direction with E-field polarization in x-direction.

The point and the returned field are in Cartesian coordinates.
