```
sle_solubility(model::CompositeModel, p, T, z; solute)
```

Calculates the solubility of each component within a solution of the other components, at a given temperature and composition. Returns a matrix containing the composition of the SLE phase boundary for each component. If `solute` is specified, returns only the solubility of the specified component.

Can only function when solid and fluid models are specified within a CompositeModel.
