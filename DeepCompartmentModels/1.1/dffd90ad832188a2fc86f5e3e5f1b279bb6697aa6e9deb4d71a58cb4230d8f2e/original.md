```
two_comp!(dA, A, p, t)
```

In-place function for the two-compartment model:

```
dA₁/dt = (I / V₁) + A₂ ⋅ k₂₁ - A₁ ⋅ (k₁₀ + k₁₂)
dA₂/dt = A₁ ⋅ k₁₂ - A₂ ⋅ k₂₁
```

# Model Parameters

  * `CL`: Drug clearance from the first compartment.
  * `V₁`: Central volume of distribution (in A₁).
  * `Q`: Inter-compartmental clearance.
  * `V₂`: Peripheral volume of distribution (in A₂).
  * `I`: Rate of drug infusion; handled by callback function.

# Inferred parameters

  * `k₁₀`: CL / V₁
  * `k₁₂`: Q / V₁
  * `k₂₁`: Q / V₂
