```
struct NoisySchrodingerEquation
```

Decorator object for SchrodingerEquation. Implements the f(dstate, state, p, t) interface to fit into a standard ODE Problem.

# Arguments

  * `equation`: The coherent 'SchrodingerEquation` equation for the problem
  * `imag_evo`: ∑_L L^†L for collapse operators L which defines the non-hermitian part of the Hamiltonian
  * `num_cops``: number of collapse operators (for displaying)
