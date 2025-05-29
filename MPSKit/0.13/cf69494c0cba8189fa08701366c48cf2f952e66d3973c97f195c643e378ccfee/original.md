```
fidelity_susceptibility(state::Union{FiniteMPS,InfiniteMPS}, H₀::T,
                        Vs::AbstractVector{T}, [henvs=environments(state, H₀)];
                        maxiter=Defaults.maxiter,
                        tol=Defaults.tol) where {T<:MPOHamiltonian}
```

Computes the fidelity susceptibility of a the ground state `state` of a base Hamiltonian `H₀` with respect to a set of perturbing Hamiltonians `Vs`. Each of the perturbing Hamiltonians can be interpreted as corresponding to a tuning parameter $aᵢ$ in a 'total' Hamiltonian $H = H₀ + ∑ᵢ aᵢ Vᵢ$.

Returns a matrix containing the overlaps of the elementary excitations on top of `state` corresponding to each of the perturbing Hamiltonians.
