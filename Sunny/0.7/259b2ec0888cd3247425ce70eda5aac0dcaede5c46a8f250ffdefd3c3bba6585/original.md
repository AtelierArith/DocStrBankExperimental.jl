```
ImplicitMidpoint(dt::Float64; atol=1e-12) where N
```

The implicit midpoint method for integrating the Landau-Lifshitz spin dynamics or its generalization to SU(*N*) coherent states [1]. One call to the [`step!`](@ref) function will advance a [`System`](@ref) by `dt` units of time. This integration scheme is exactly symplectic and eliminates energy drift over arbitrarily long simulation trajectories.

## References

1. [H. Zhang and C. D. Batista, *Classical spin dynamics based on SU(N) coherent states*, Phys. Rev. B **104**, 104409 (2021)](https://doi.org/10.1103/PhysRevB.104.104409).
