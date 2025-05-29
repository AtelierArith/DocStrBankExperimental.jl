```
ibmmpo(ω0, d, N, chainparams; tree=false)
```

Generate MPO for a spin-1/2 coupled to a chain of harmonic oscillators with the interacting boson model (IBM), defined by the Hamiltonian

$H = \frac{ω_0}{2}σ_z +  c_0σ_z(b_0^\dagger+b_0) + \sum_{i=0}^{N-1} t_i (b_{i+1}^\dagger b_i +h.c.) + \sum_{i=0}^{N} ϵ_ib_i^\dagger b_i$.

The spin is on site 1 of the MPS and the bath modes are to the right.

This Hamiltonain is unitarily equivalent (before the truncation to `N` sites) to the spin-boson Hamiltonian defined by

$H =  \frac{ω_0}{2}σ_z + σ_z\int_0^∞ dω\sqrt{J(ω)}(b_ω^\dagger+b_ω) + \int_0^∞ dω ωb_ω^\dagger b_ω$.

The chain parameters, supplied by `chainparams`=$[[ϵ_0,ϵ_1,...],[t_0,t_1,...],c_0]$, can be chosen to represent any arbitrary spectral density $J(ω)$ at any temperature.
