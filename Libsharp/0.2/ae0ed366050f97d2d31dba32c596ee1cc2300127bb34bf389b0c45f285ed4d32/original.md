```
make_triangular_alm_info(lmax::Integer, mmax::Integer, stride::Integer)
```

Initialises an a*lm data structure according to the scheme  used by Healpix*cxx.

# Arguments

  * `lmax::Integer`: maximum spherical harmonic ℓ
  * `mmax::Integer`: maximum spherical harmonic m
  * `stride::Integer`: the stride between consecutive pixels in the ring

# Returns

  * `AlmInfo` object
