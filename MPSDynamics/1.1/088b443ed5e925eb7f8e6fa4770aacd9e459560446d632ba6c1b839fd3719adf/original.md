```
twobathspinmpo(ω0, Δ, Nl, Nr, dl, dr, chainparamsl=[fill(1.0,N),fill(1.0,N-1), 1.0], chainparamsr=chainparamsl; tree=false)
```

Generate MPO for a spin-1/2 coupled to two chains of harmonic oscillators, defined by the Hamiltonian

$H = \frac{ω_0}{2}σ_z + Δσ_x + c_0^rσ_x(b_0^\dagger+b_0) + \sum_{i=0}^{N_r-1} t_i^r (b_{i+1}^\dagger b_i +h.c.) + \sum_{i=0}^{N_r} ϵ_i^rb_i^\dagger b_i + c_0^lσ_x(d_0^\dagger+d_0) + \sum_{i=0}^{N_l-1} t_i^l (d_{i+1}^\dagger d_i +h.c.) + \sum_{i=0}^{N_l} ϵ_i^l d_i^\dagger d_i$.

The spin is on site $N_l + 1$ of the MPS, surrounded by the left chain modes and the right chain modes.

This Hamiltonain is unitarily equivalent (before the truncation to `N` sites) to the spin-boson Hamiltonian defined by

$H =  \frac{ω_0}{2}σ_z + Δσ_x + σ_x\int_0^∞ dω\sqrt{J(ω)}(b_ω^\dagger+b_ω) + \int_0^∞ dω ωb_ω^\dagger b_ωi + σ_x\int_0^∞ dω\sqrt{J^l(ω)}(d_ω^\dagger+d_ω) + \int_0^∞ dω ωd_ω^\dagger d_ω$.

The chain parameters, supplied by `chainparams`=$[[ϵ_0,ϵ_1,...],[t_0,t_1,...],c_0]$, can be chosen to represent any arbitrary spectral density $J(ω)$ at any temperature. The two chains can have a different spectral density.
