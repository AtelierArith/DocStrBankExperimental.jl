```
azlcpo(target, et, abcorr, obspos, obsctr, obsref;
       method="ELLIPSOID", azccw=true, elplsz=true)
```

Return the azimuth/elevation coordinates of a specified target relative to an "observer," where the observer has constant position in a specified reference frame. The observer's position is provided by the calling program rather than by loaded SPK files.

### Arguments

  * `target`: Name of target ephemeris object
  * `et`: Observation epoch
  * `abcorr`: Aberration correction
  * `obspos`: Observer position relative to center of motion
  * `obsctr`: Center of motion of observer
  * `obsref`: Body-fixed, body-centered frame of observer's center

### Keyword Arguments

  * `method`: Method to obtain the surface normal vector. The only (and default) choice currently supported is `"ELLIPSOID"`
  * `azccw`: Flag indicating how azimuth is measured. If `true` (the default), the azimuth increases in the counterclockwise direction; otherwise it increases in the clockwise direction
  * `elplsz`: Flag indicating how elevation is measured. If `true` (the default), the elevation increases from the XY plane toward +Z; otherwise toward -Z

### Output

  * `azlsta`: State of target with respect to observer, in azimuth/elevation coordinates: `azlsta = [r, az, el, dr/dt, daz/dt, del/dt]`
  * `lt`: One-way light time between target and observer

### References

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/azlcpo_c.html)
