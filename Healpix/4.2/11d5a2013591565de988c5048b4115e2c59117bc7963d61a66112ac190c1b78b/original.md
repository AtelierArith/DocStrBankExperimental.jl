```
almxfl!(alm::Alm{Complex{T}}, fl::AA) where {T <: Number,AA <: AbstractArray{T,1}}
```

Multiply IN-PLACE an a*ℓm by a vector b*ℓ representing an ℓ-dependent function.

# ARGUMENTS

  * `alms::Alm{Complex{T}}`: The `Alm` object containing the spherical harmonics coefficients
  * `fl::AbstractVector{T}`: The array containing the factors f*ℓ to be multiplied by a*ℓm
