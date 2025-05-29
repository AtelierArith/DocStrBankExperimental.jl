```
ElectrostaticParticlePush(species, E, timestep, [interpolation_order=1])
```

An update step that moves and accelerates particles of `species` according to the electric field `E`. The field will be interpolated to the particle positions using b-splines of `interpolation_order`.
