```
scatteredfield(sphere::LayeredSpherePEC, excitation::UniformField, point, quantity::ElectricField; parameter::Parameter=Parameter())
```

Compute the electric field scattered by a layered dielectric sphere with PEC core, for an incident uniform field with polarization in the given direction using `Sihvola and Lindell, 1988, Transmission line analogy for calculating the effective permittivity of mixtures with spherical multilayer scatterers`.

In contrast to `Sihvola and Lindell` the radii of the shells are ordered from inside to outside as depicted in the documentation.

The point and returned field are in Cartesian coordinates.
