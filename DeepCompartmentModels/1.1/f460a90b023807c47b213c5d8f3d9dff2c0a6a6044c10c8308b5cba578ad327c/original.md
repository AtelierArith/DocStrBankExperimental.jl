```
one_comp!(dA, A, p, t)
```

In-place function for the one-compartment model: `dA/dt = (I / Vd) - A₁ ⋅ k₁₀`

# Model parameters

  * `CL`: Drug clearance estimate.
  * `Vd`: Drug volume of distribution estimate.
  * `I`: Rate of drug infusion; handled by callback function.

# Inferred parameters

  * `k₁₀`: CL / Vd
