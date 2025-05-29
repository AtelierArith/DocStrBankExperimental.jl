```
one_comp_abs!(dA, A, p, t)
```

In-place function for the one-compartment model with an absorption compartment:

```
dA₁/dt = I - kₐ ⋅ A₁
dA₂/dt = kₐ ⋅ A₁ - A₂ ⋅ k₁₀
```

# Model parameters

  * `kₐ`: Rate of drug absorption.
  * `CL`: Drug clearance estimate.
  * `Vd`: Drug volume of distribution estimate.
  * `I`: Rate of drug infusion; handled by callback function.
