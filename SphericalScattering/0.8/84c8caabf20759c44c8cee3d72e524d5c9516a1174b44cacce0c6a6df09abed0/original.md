```
scatteredfield(sphere::PECSphere, excitation::UniformField, point, quantity::ElectricField; parameter::Parameter=Parameter())
```

Compute the electric field scattered by a PEC sphere, for an incident uniform field with polarization in the given direction.

The point and returned field are in Cartesian coordinates.
