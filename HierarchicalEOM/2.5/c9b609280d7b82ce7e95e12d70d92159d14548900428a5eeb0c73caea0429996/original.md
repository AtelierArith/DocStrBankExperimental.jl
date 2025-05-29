```
Boson_Underdamped_Matsubara(op, λ, W, ω0, kT, N)
```

Construct an underdamped bosonic bath with Matsubara expansion

# Parameters

  * `op` : The system coupling operator, must be Hermitian and, for fermionic systems, even-parity to be compatible with charge conservation.
  * `λ::Real`: The coupling strength between the system and the bath.
  * `W::Real`: The band-width of the bath spectral density.
  * `ω0::Real`: The resonance frequency of the bath spectral density.
  * `kT::Real`: The product of the Boltzmann constant $k$ and the absolute temperature $T$ of the bath.
  * `N::Int`: (N+2)-terms of exponential terms are used to approximate the bath correlation function.

# Returns

  * `bath::BosonBath` : a bosonic bath object with describes the interaction between system and bosonic bath
