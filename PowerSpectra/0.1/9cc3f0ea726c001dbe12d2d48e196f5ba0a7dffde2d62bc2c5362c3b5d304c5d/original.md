```
synalm!([rng=GLOBAL_RNG], Cl::AbstractArray{T,3}, alms) where T
```

In-place synthesis of spherical harmonic coefficients, given spectra.

# Arguments:

  * `Cl::AbstractArray{T,3}`: array with dimensions of comp, comp, ℓ
  * `alms::Union{NTuple{N,Alm}, Vector{Alm}}`: array of Alm to fill

# Examples

```julia
nside = 16
C0 = [3.  2.;  2.  5.]
Cl = repeat(C0, 1, 1, 3nside)  # spectra constant with ℓ
alms = [Alm{Complex{Float64}}(3nside-1, 3nside-1) for i in 1:2]
synalm!(Cl, alms)
```
