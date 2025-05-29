```
SalvageType
```

An enum of the type of formula for salvage value calculation.

Salvage values assigns a negative cost to Microgrid components which have a *residual lifetime* at the end of the project.

## Values

Possible values are:

  * `LinearSalvage`: salvage value proportional to residual lifetime
  * `ConsistentSalvage`: salvage value depends nonlinearly in the residual lifetime such that it is economically consistent.

Economic consistency means that, using this nonlinear formula, the NPC computation for a given component (investment + replacement(s) - salvage) is consistent with the annualized component cost computation (investment*CRF(component lifetime)).

Remark: zero salvage value can be obtained by setting `salvage_price_ratio=0.0` for each Microgrid component.
