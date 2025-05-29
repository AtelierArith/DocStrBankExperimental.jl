```
Langevin(dt::Float64; damping::Float64, kT::Float64)
```

An integrator for Langevin spin dynamics using the explicit Heun method. The `damping` parameter controls the coupling to an implicit thermal bath. One call to the [`step!`](@ref) function will advance a [`System`](@ref) by `dt` units of time. Can be used to sample from the Boltzmann distribution at temperature `kT`. An alternative approach to sampling states from thermal equilibrium is [`LocalSampler`](@ref), which proposes local Monte Carlo moves. For example, use `LocalSampler` instead of `Langevin` to sample Ising-like spins.

Setting `damping = 0` disables coupling to the thermal bath, yielding an energy-conserving spin dynamics. The `Langevin` integrator uses an explicit numerical integrator which cannot prevent energy drift. Alternatively, the [`ImplicitMidpoint`](@ref) method can be used, which is more expensive but prevents energy drift through exact conservation of the symplectic 2-form.

If the [`System`](@ref) has `mode = :dipole`, then the dynamics is the stochastic Landau-Lifshitz equation,

$$
    d𝐒/dt = -𝐒 × (ξ - 𝐁 + λ 𝐒 × 𝐁),
$$

where $𝐁 = -dE/d𝐒$ is the effective field felt by the expected spin dipole $𝐒$. The components of $ξ$ are Gaussian white noise, with magnitude $√(2 k_B T λ)$ set by a fluctuation-dissipation theorem. The parameter `damping` sets the phenomenological coupling $λ$ to the thermal bath.

If the `System` has `mode = :SUN`, then this dynamics generalizes [1] to a stochastic nonlinear Schrödinger equation for SU(*N*) coherent states $𝐙$,

$$
    d𝐙/dt = -i P [ζ + (1 - i λ̃) ℋ 𝐙].
$$

Here, $P$ projects onto the space orthogonal to $𝐙$, and $ζ$ denotes complex Gaussian white noise with magnitude $√(2 k_B T λ̃)$. The local-Hamiltonian $ℋ$ embeds the energy gradient into the 𝔰𝔲(*N*) Lie algebra, and generates evolution of spin dipoles, quadrupoles, etc. The parameter `damping` here sets $λ̃$, which is analogous to $λ$ above.

When applied to SU(2) coherent states, the generalized spin dynamics reduces exactly to the stochastic Landau-Lifshitz equation. The mapping is as follows. Normalized coherent states $𝐙$ map to dipole expectation values $𝐒 = 𝐙^{†} Ŝ 𝐙$, where spin operators $Ŝ$ are a spin-$|𝐒|$ representation of SU(2). The local effective Hamiltonian $ℋ = -𝐁 ⋅ Ŝ$ generates rotation of the dipole in analogy to the vector cross product $S × 𝐁$. The coupling to the thermal bath maps as $λ̃ = |𝐒| λ$. Note, therefore, that the scaling of the `damping` parameter varies subtly between `:dipole` and `:SUN` modes.

## References

1. [D. Dahlbom et al., *Langevin dynamics of generalized spins as SU(N) coherent states*, Phys. Rev. B **106**, 235154 (2022)](https://doi.org/10.1103/PhysRevB.106.235154).
