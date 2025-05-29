```
fidelity(Ψ::MPS, ϱ::LPDO{MPO}; cutoff::Float64 = 1e-15)
fidelity(ϱ::LPDO{MPO}, ψ::MPS; kwargs...)
```

Quantum state fidelity between an MPS wavefunction and a LPDO density operator $\varrho=XX^\dagger$

$$
F(\psi,\rho) = \langle\psi|\varrho|\psi\rangle = |X^\dagger|\psi\rangle|^2.
$$
