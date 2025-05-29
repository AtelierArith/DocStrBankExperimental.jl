```
calc_exchanges(hamiltonian::TBHamiltonian, atoms::Vector{<:Atom}, fermi, exchange_type; kwargs...)
```

Calculates the magnetic exchange parameters between the `atoms`. `exchange_type` can be [`Exchange2ndOrder`](@ref) or [`Exchange4thOrder`](@ref). The `kwargs` control various numerical parameters for the calculation:

  * `nk = (10,10,10)`: the amount of *k*-points to be used for the uniform interpolation grid.
  * `R = (0,0,0)`: the unit cell index to which the exchange parameters are calculated.
  * `ωh = -30.0`: the lower bound of the energy integration
  * `ωv = 0.15`: the height of the contour in complex space to integrate the Green's functions
  * `n_ωh = 3000`: number of integration points along the horizontal contour direction
  * `n_ωv = 500`: number of integration points along the vertical contour direction
  * `site_diagonal = false`: if `true` the hamiltonians and `Δ` will diagonalized on-site and the

returned exchange matrices hold the exchanges between well-defined orbitals. If this is not done, the exchange matrices entries don't mean anything on themselves and a trace should be performed to find the exchange between the spins on sites `i` and `j`.
