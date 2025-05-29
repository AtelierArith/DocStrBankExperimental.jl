```
struct NoisySchrodingerEquation
NoisySchrodingerEquation(reg, tspan, hamiltonian, c_ops; kw...)
NoisySchrodingerEquation(reg, tspan, hamiltonian, noise_model; kw...)
```

Define an ODE Problem representing a single noisy trajectory in an open system in the weak-coupling limit

# Arguments

  * `reg`: evolution register and initial state of the problem
  * `tspan`: a vector of times at which to save the simulation
  * `hamiltonian`: AbstractBlock such as that produced by `rydberg_h``    representing evolution hamiltonian
