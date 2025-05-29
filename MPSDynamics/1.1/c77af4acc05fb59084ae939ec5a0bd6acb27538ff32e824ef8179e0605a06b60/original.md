```
chaincoeffs_ohmic(N, α, s; ωc=1, soft=false)
```

Generate chain coefficients $[[ϵ_0,ϵ_1,...],[t_0,t_1,...],c_0]$ for an Harmonic bath at zero temperature with a power law spectral density given by:

soft cutoff: $J(ω) = 2αω_c (\frac{ω}{ω_c})^s \exp(-ω/ω_c)$ 

hard cutoff: $J(ω) = 2αω_c (\frac{ω}{ω_c})^s θ(ω-ω_c)$

The coefficients parameterise the chain Hamiltonian

$H = H_S + c_0 A_S⊗B_0+\sum_{i=0}^{N-1}t_i (b_{i+1}^\dagger b_i +h.c.) + \sum_{i=0}^{N} ϵ_ib_i^\dagger b_i$

which is unitarily equivalent (before the truncation to `N` sites) to

$H = H_S + A_S⊗\int_0^∞dω\sqrt{J(ω)}B_ω + \int_0^∞dωωb_ω^\dagger b_ω$.
