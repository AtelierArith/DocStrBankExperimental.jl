```julia
KineticEnergyStressTerm(model; location)

```

Return a `KernelFunctionOperation` that computes the diffusive term of the KE prognostic equation:

```
    DIFF = uᵢ∂ⱼτᵢⱼ
```

where `uᵢ` are the velocity components and `τᵢⱼ` is the diffusive flux of `i` momentum in the  `j`-th direction.
