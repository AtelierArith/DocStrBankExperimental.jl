```
two_comp_abs!(dA, A, p, t)
```

In-place function for the two-compartment model with an absorption compartment:

```
dA₁/dt = I - kₐ ⋅ A₁
dA₂/dt = kₐ ⋅ A₁ + A₃ ⋅ k₃₂ - A₂ ⋅ (k₂₀ + k₂₃)
dA₃/dt = A₂ ⋅ k₂₃ - A₃ ⋅ k₃₂
```

# Model parameters

  * `kₐ`: Rate of drug absorption.
  * `CL`: Drug clearance from the first compartment (in A₂).
  * `V₁`: Central volume of distribution (in A₂).
  * `Q`: Inter-compartmental clearance (in A₃).
  * `V₂`: Peripheral volume of distribution (in A₃).
  * `I`: Rate of drug infusion; handled by callback function.
