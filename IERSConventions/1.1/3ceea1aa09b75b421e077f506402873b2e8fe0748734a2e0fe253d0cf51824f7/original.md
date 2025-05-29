```
iers_precession(m::IERSModel, tt_c::Number)
```

Return the precession matrix that rotates a vector from MEME2000 axes to Mean of Date (MOD)  axes, at time `tt_c` expressed in `TT` Julian centuries since `J2000`, according to the IERS  convention `m`. 

!!! note
    This matrix rotates vectors from the Mean Equator and Mean Equinox of J2000 (MEME2000)  to Mean-of-Date (MOD) axes. The frame bias between the GCRF and MEME2000 is excluded  from the returned matrix and must eventually be included with a separate rotation.


!!! note
    The IAU Working Group on Precession and the Ecliptic (Hilton, 2006) has decided to leave  the choice of the parameterization for the precession angles to the user. In this  function for the IERS 1996 conventions, the precession matrix is computed using the  traditional parameterization of Newcomb and Liekse (`zₐ`, `θₐ`, `ζₐ`), whereas it adopts  the 4-angles formulation (`ϵ₀`, `ψₐ`, `ωₐ`, `χₐ`) recommended by (Capitaine et al., 2003a) for all the remaining models.


### References

  * Lieske J. H. et al, (1977), Expression for the Precession Quantities Based upon the IAU    (1976) System of Astronomical Constants.
  * Hilton J. L. et al., (2006), Report of the International Astronomical Union Division I Working    Group on Precession and the Ecliptic.
  * Capitaine N. et al., (2003a), Expressions for IAU 2000 precession quantities.
  * IERS Technical Note No. [21](https://www.iers.org/IERS/EN/Publications/TechnicalNotes/tn21.html)
  * IERS Technical Note No. [32](https://www.iers.org/IERS/EN/Publications/TechnicalNotes/tn32.html)
  * IERS Technical Note No. [36](https://www.iers.org/IERS/EN/Publications/TechnicalNotes/tn36.html)

### See also

See also [`precession_angles_rot3`](@ref) and [`precession_angles_rot4`](@ref)
