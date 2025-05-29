```
BoundaryModelTafuni()
```

Boundary model for the `OpenBoundarySPHSystem`. This model implements the method of [Tafuni et al. (2018)](@cite Tafuni2018) to extrapolate the properties from the fluid domain to the buffer zones (inflow and outflow) using ghost nodes. The position of the ghost nodes is obtained by mirroring the boundary particles into the fluid along a direction that is normal to the open boundary.
