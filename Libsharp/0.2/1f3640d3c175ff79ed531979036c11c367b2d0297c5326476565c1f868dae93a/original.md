```
make_alm_info(lmax::Integer, mmax::Integer, stride::Integer, 
    mstart::AbstractArray{T}) where T <: Integer
```

Initialises a general a_lm data structure.

# Arguments

  * `lmax::Integer`: maximum spherical harmonic ℓ
  * `mmax::Integer`: maximum spherical harmonic m
  * `stride::Integer`: the stride between consecutive pixels in the ring
  * `mstart::AbstractArray{T}`: index of the coefficient with the quantum    numbers 0, m. Must have mmax+1 entries.

# Returns

  * AlmInfo object
