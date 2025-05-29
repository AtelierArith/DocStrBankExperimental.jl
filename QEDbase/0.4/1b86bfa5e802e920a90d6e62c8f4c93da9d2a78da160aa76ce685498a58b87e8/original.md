```
propagator(particle::AbstractParticleType, mom::QEDbase.AbstractFourMomentum)
```

Compute the propagator of a particle for a given four-momentum `mom`.

# Notes on Convention

The `QEDProcesses.jl` package includes two types of propagators:

**Boson-like particles**: For a `BosonLike` particle with four-momentum `k` and mass `m = QEDbase.mass(particle)`, the propagator is given by:

$$
D(k) = \frac{1}{k^2 - m^2}
$$

**Fermion-like particles**: For a `FermionLike` particle with four-momentum `p` and mass `m = QEDbase.mass(particle)`, the propagator is defined as:

$$
S(p) = \frac{\gamma^\mu p_\mu + m}{p^2 - m^2}
$$

Here, $\gamma^\mu$ are the gamma matrices, and $p_\mu$ represents the four-momentum components.

!!! warning
    This function does **not** throw an error if the particle is off-shell (i.e., if it does not satisfy the mass-shell condition). In such cases, the function will return `Inf`, which indicates that the propagator is undefined for an off-shell particle.

