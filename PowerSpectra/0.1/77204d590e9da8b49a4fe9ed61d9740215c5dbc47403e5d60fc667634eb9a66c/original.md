```
synalm([rng=GLOBAL_RNG], Cl::AbstractArray{T,3}, nside::Int) where T
```

# Arguments:

  * `Cl::AbstractArray{T,3}`: array with dimensions of comp, comp, ℓ
  * `nside::Int`: healpix resolution

# Returns:

  * `Vector{Alm{T}}`: spherical harmonics realizations for each component

# Examples

```julia
nside = 16
C0 = [3.  2.;  2.  5.]
Cl = repeat(C0, 1, 1, 3nside)  # spectra constant with ℓ
alms = synalm(Cl, nside)
```
