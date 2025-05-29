```
alm2cl(alm::Alm{Complex{T}}) where {T <: Number} -> Vector{T}
alm2cl(alm₁::Alm{Complex{T}}, alm₂::Alm{Complex{T}}) where {T <: Number} -> Vector{T}
```

Compute $C_{\ell}$ from the spherical harmonic coefficients of one or two fields.

# Arguments

  * `alm₁::Alm{Complex{T}}`: the spherical harmonic coefficients of the first field
  * `alm₂::Alm{Complex{T}}`: the spherical harmonic coefficients of the second field

# Returns

  * `Array{T}` containing $C_{\ell}$, with the first element referring to ℓ=0.
