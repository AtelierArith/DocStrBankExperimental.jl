```
iers_bias(m::IERSModel, tt_c::Number)
```

Compute the frame bias matrix, which transform vectors from the GCRF axes to the Mean  Equinox and Mean Equator of J2000 (MEME2000) axes. 

!!! note
    Since in the IERS 1996 conventions the bias matrix was still undefined, the returned  matrix is the identity.


### References

  * IERS Technical Note No. [21](https://www.iers.org/IERS/EN/Publications/TechnicalNotes/tn21.html)
  * IERS Technical Note No. [32](https://www.iers.org/IERS/EN/Publications/TechnicalNotes/tn32.html)
  * IERS Technical Note No. [36](https://www.iers.org/IERS/EN/Publications/TechnicalNotes/tn36.html)

### See also

See also [`iers_precession`](@ref), [`iers_pb`](@ref) and [`iers_npb`](@ref).
