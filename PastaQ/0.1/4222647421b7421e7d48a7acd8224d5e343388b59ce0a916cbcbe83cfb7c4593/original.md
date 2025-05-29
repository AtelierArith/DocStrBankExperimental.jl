```
fidelity(ψ::MPS, ρ::MPO; kwargs...)
fidelity(ρ::MPO, ψ::MPS; kwargs...)
```

Quantum state fidelity between an MPS wavefunction and an MPO density operator:

$$
F(\psi,\rho) = \langle\psi|\rho|\psi\rangle.
$$
