```
scatteredfield(sphere::PECSphere, excitation::Dipole, point, quantity::MagneticField; parameter::Parameter=Parameter())
```

Compute the magnetic field scattered by a PEC sphere, where the dipole is placed along the z-axis at z0.

The point and the returned field are in Cartesian coordinates.
