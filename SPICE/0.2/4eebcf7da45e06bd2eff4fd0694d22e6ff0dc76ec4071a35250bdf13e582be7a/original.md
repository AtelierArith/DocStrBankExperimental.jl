```
illumf(method, target, ilusrc, et, fixref, abcorr, obsrvr, spoint)
```

Compute the illumination angles - phase, incidence, and emission - at a specified point on a target body. Return logical flags indicating whether the surface point is visible from the observer's position and whether the surface point is illuminated.

The target body's surface is represented using topographic data provided by DSK files, or by a reference ellipsoid.

The illumination source is a specified ephemeris object.

### Arguments

  * `method`: Computation method
  * `target`: Name of target body
  * `ilusrc`: Name of illumination source
  * `et`: Epoch in TDB seconds past J2000 TDB
  * `fixref`: Body-fixed, body-centered target body frame
  * `abcorr`: Aberration correction flag
  * `obsrvr`: Name of observing body
  * `spoint`: Body-fixed coordinates of a target surface point

### Output

  * `trgepc`: Target surface point epoch
  * `srfvec`: Vector from observer to target surface point
  * `phase`: Phase angle at the surface point
  * `incdnc`: Source incidence angle at the surface point
  * `emissn`: Emission angle at the surface point
  * `visibl`: Visibility flag (`true` if visible)
  * `lit`: Illumination flag (`true` if illuminated)

### References

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/illumf_c.html)
