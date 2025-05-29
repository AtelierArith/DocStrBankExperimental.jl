```
scatteredfield(sphere::DielectricSphereThinImpedanceLayer, excitation::UniformField, point, quantity::ElectricField; parameter::Parameter=Parameter())
```

Compute the electric field scattered by a dielectric sphere with a thin coating, where the displacement field in the coating is only in radial direction. We assume an an incident uniform field with polarization in the given direction.

The point and the returned field are in Cartesian coordinates.
