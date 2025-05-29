```
baryvel(dje, deq) -> dvelh, dvelb
```

### Purpose

Calculates heliocentric and barycentric velocity components of Earth.

### Explanation

Baryvel takes into account the Earth-Moon motion, and is useful for radial velocity work to an accuracy of ~1 m/s.

### Arguments

  * `dje`: julian ephemeris date
  * `deq` (optional): epoch of mean equinox of `dvelh` and `dvelb`. If `deq` is not provided, then it is assumed to be equal to `dje`.

### Output

  * `dvelh`: heliocentric velocity component. in km/s
  * `dvelb`: barycentric velocity component. in km/s

### Example

Compute the radial velocity of the Earth toward Altair on 15-Feb-1994 using both the original Stumpf algorithm.

```jldoctest
julia> using AstroLib

julia> jd = jdcnv(1994, 2, 15, 0)
2.4493985e6

julia> baryvel(jd, 2000)
([-17.0724258266945, -22.81120895274765, -9.889315408506354], [-17.080834081384847, -22.80470807516409, -9.886258269159352])
```

### Notes

The 3-vectors outputs `dvelh` and `dvelb` are given in a right-handed coordinate system with the +X axis toward the Vernal Equinox, and +Z axis toward the celestial pole.

Code of this function is based on IDL Astronomy User's Library.
