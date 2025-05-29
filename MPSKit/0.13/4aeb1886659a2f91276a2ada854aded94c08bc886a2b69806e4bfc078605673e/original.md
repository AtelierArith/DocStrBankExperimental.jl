```
propagator(ψ₀::AbstractFiniteMPS, z::Number, H::MPOHamiltonian, alg::DynamicalDMRG; init=copy(ψ₀))
```

Calculate the propagator $\frac{1}{E₀ + z - H}|ψ₀⟩$ using the dynamical DMRG algorithm.
