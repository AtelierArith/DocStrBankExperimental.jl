```
ChargeBasis(ncut) <: Basis
```

Basis spanning `-ncut, ..., ncut` charge states, which are the fourier modes (irreducible representations) of a continuous U(1) degree of freedom, truncated at `ncut`.

The charge basis is a natural representation for circuit-QED elements such as the "transmon", which has a hamiltonian of the form

```julia
b = ChargeBasis(ncut)
H = 4E_C * (n_g * identityoperator(b) + chargeop(b))^2 - E_J * cosφ(b)
```

with energies periodic in the charge offset `n_g`. See e.g. https://arxiv.org/abs/2005.12667.
