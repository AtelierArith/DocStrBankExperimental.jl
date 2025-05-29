```
Boson_DrudeLorentz_Pade(op, λ, W, kT, N)
```

Constructing Drude-Lorentz bosonic bath with Padé expansion

A Padé approximant is a sum-over-poles expansion (see [here](https://en.wikipedia.org/wiki/Pad%C3%A9_approximant) for more details).

The application of the Padé method to spectrum decompoisitions is described in Ref. [1].

[1] [J. Chem. Phys. 134, 244106 (2011)](https://doi.org/10.1063/1.3602466)

# Parameters

  * `op` : The system coupling operator, must be Hermitian and, for fermionic systems, even-parity to be compatible with charge conservation.
  * `λ::Real`: The coupling strength between the system and the bath.
  * `W::Real`: The reorganization energy (band-width) of the bath.
  * `kT::Real`: The product of the Boltzmann constant $k$ and the absolute temperature $T$ of the bath.
  * `N::Int`: (N+1)-terms of exponential terms are used to approximate the bath correlation function.

# Returns

  * `bath::BosonBath` : a bosonic bath object with describes the interaction between system and bosonic bath
