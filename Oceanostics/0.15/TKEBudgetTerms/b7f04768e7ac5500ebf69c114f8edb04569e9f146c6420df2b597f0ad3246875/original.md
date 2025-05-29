```julia
KineticEnergyForcingTerm(model; location)

```

Return a `KernelFunctionOperation` that computes the forcing term of the KE prognostic equation:

```
    FORC = uᵢFᵤᵢ
```

where `uᵢ` are the velocity components and `Fᵤᵢ` is the forcing term(s) in the `uᵢ` prognostic equation (i.e. the forcing for `uᵢ`).
