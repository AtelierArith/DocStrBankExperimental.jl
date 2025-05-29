```
anafast(map::HealpixMap{Float64, RingOrder, AA}; lmax=nothing, mmax=nothing, niter::Integer = 3) where {T <: Real,AA <: AbstractArray{T,1}} -> Vector{Float64}
anafast(map₁::HealpixMap{Float64, RingOrder, AA}, map₂::HealpixMap{Float64, RingOrder, AA}; lmax=nothing, mmax=nothing, niter::Integer = 3) where {T <: Real,AA <: AbstractArray{T,1}} -> Vector{Float64}
```

Computes the power spectrum of a Healpix map, or the cross-spectrum between two maps if `map2` is given. No removal of monopole or dipole is performed. The input maps must be in ring-ordering.

# Arguments:

  * `map₁::HealpixMap{Float64, RingOrder, AA}`: the spherical harmonic coefficients of the first field
  * `map₂::HealpixMap{Float64, RingOrder, AA}`: the spherical harmonic coefficients of the second field

# Returns:

  * `Array{T}` containing $C_{\ell}$, with the first element referring to ℓ=0.
