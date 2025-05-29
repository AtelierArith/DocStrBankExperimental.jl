```
minimize_spiral_energy!(sys, axis; maxiters=10_000, k_guess=randn(sys.rng, 3))
```

Finds a generalized spiral order that minimizes the [`spiral_energy`](@ref). This involves optimization of the spin configuration in `sys`, and the propagation wavevector $𝐤$, which will be returned in reciprocal lattice units (RLU). The `axis` vector normal to the polarization plane cannot yet be optimized; it should be determined according to symmetry considerations and provided in global Cartesian coordinates. The initial `k_guess` will be random, unless otherwise provided.

See also [`suggest_magnetic_supercell`](@ref) to find a system shape that is approximately commensurate with the returned propagation wavevector $𝐤$.
