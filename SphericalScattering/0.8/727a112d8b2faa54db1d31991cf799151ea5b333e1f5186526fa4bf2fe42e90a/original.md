```
scatteredfield(sphere::DielectricSphereThinImpedanceLayer, excitation::UniformField, point, quantity::ScalarPotentialJump; parameter::Parameter=Parameter())
```

Compute the jump of the scalar potential for a dielectric sphere with a thin coating, where the displacement field in the coating is only in radial direction. We assume an an incident uniform field with polarization in the given direction.

More precisely, we compute the difference Δ = Φ*i - Φ*e, where Φ*i is the potential on the inner side and ϕ*e the exterior potential.

The point and the returned field are in Cartesian coordinates.
