```
almxfl(alm::Alm{Complex{T}}, fl::AbstractVector{T}) where {T <: Number} -> Alm{T}
```

Multiply an a*ℓm by a vector b*ℓ representing an ℓ-dependent function, without changing the a_ℓm passed in input.

# ARGUMENTS

  * `alms::Alm{Complex{T}}`: The `Alm` object containing the spherical harmonics coefficients
  * `fl::AbstractVector{T}`: The array containing the factors f*ℓ to be multiplied by a*ℓm

#RETURNS

  * `Alm{Complex{T}}`: The result of a*ℓm * f*ℓ.
