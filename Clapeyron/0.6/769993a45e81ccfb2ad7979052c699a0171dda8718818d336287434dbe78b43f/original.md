```
slle_solubility(model::CompositeModel, p, T)
```

Calculates the phase boundary for solid-liquid-liquid equilibriumm of a **ternary** mixture, at a given temperature and pressure. Returns a matrix containing the composition of the two liquids phases.

Can only function when solid and liquid models are specified within a CompositeModel and when the third component is the solute.
