```
Boson_DrudeLorentz_Matsubara(op, λ, W, kT, N)
```

Constructing Drude-Lorentz bosonic bath with Matsubara expansion

# Parameters

  * `op` : The system coupling operator, must be Hermitian and, for fermionic systems, even-parity to be compatible with charge conservation.
  * `λ::Real`: The coupling strength between the system and the bath.
  * `W::Real`: The reorganization energy (band-width) of the bath.
  * `kT::Real`: The product of the Boltzmann constant $k$ and the absolute temperature $T$ of the bath.
  * `N::Int`: (N+1)-terms of exponential terms are used to approximate the bath correlation function.

# Returns

  * `bath::BosonBath` : a bosonic bath object with describes the interaction between system and bosonic bath
