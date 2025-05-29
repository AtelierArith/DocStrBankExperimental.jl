```
Fermion_Lorentz_Matsubara(op, λ, μ, W, kT, N)
```

Constructing Lorentzian fermionic bath with Matsubara expansion

# Parameters

  * `op` : The system annihilation operator according to the system-fermionic-bath interaction.
  * `λ::Real`: The coupling strength between the system and the bath.
  * `μ::Real`: The chemical potential of the bath.
  * `W::Real`: The reorganization energy (band-width) of the bath.
  * `kT::Real`: The product of the Boltzmann constant $k$ and the absolute temperature $T$ of the bath.
  * `N::Int`: (N+1)-terms of exponential terms are used to approximate each correlation functions ($C^{\nu=\pm}$).

# Returns

  * `bath::FermionBath` : a fermionic bath object with describes the interaction between system and fermionic bath
