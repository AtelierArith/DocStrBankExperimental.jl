krichevskii_parameter(model::EoSModel, T, crit = nothing)

Calculates the krichevskii parameter,defined as:

```
∂p/∂x₂ |T → Tc₁,V → Vc₁, x₂ → 0
```

where the first component is the solvent and second is the solute.
