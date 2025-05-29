```
scatteredfield(sphere::PECSphere, excitation::RingCurrent, point, quantity::ElectricField; parameter::Parameter=Parameter())
```

Compute the electric field scattered by the PEC sphere, where the ring current is placed along the z-axis.

The point and the returned field are in Cartesian coordinates.
