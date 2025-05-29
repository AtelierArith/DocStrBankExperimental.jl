```
WCSTransform(naxis; kwds...)
```

Construct a WCS transformation with the given number of axes `naxis`. Keyword arguments can be passed to set various attributes of the transform. Specifying keyword arguments is equivalent to setting them after construction:

```
julia> wcs = WCSTransform(2; crpix=[1000., 1000.])
```

is equilvalent to:

```
julia> wcs = WCSTransform(2)

julia> wcs.crpix = [1000., 1000.]
```

# Properties

Below is the entire list of public properties for a `WCSTransform`

| Keyword | Type                                     | Description                                                                     |
| -------:|:---------------------------------------- |:------------------------------------------------------------------------------- |
|   naxis | `Int`                                    | Number of dimensions                                                            |
|   crval | `Vector{Float}[naxis]`                   | coordinate value at reference point                                             |
|   crpix | `Vector{Float}[naxis]`                   | array location of the reference point in pixels                                 |
|   cdelt | `Vector{Float}[naxis]`                   | coordinate increment at reference point                                         |
|   crder | `Vector{Float}[naxis]`                   | random error in coordinate                                                      |
|   csyer | `Vector{Float}[naxis]`                   | systematic error in coordinate                                                  |
|   ctype | `Vector{String}[naxis]`                  | axis type (8 characters)                                                        |
|   crota | `Vector{Float}[naxis]`                   | rotation from stated coordinate type                                            |
|   cunit | `Vector{String}[naxis]`                  | units of axes                                                                   |
|   cunit | `Vector{String}[naxis]`                  | names of axes                                                                   |
|      pc | `Matrix{Float}[naxis, naxis]`            | linear transformation matrix                                                    |
|      cd | `Matrix{Float}[naxis, naxis]`            | linear transformation matrix (with scale)                                       |
| equinox | `Float`                                  | the equinox associated with dynamical equatorial or ecliptic coordinate systems |
| latpole | `Float`                                  | the native latitude of the celestial pole                                       |
| lonpole | `Float`                                  | the native longitude of the celestial pole                                      |
|  mjdavg | `Float`                                  | Modified Julian Date corresponding to `DATE-AVG`                                |
|  mjdobs | `Float`                                  | Modified Julian Date corresponding to `DATE-OBS`                                |
| restfrq | `Float`                                  | rest frequency (Hz)                                                             |
| restwav | `Float`                                  | rest wavelength (m)                                                             |
| velangl | `Float`                                  | velocity angle                                                                  |
| velosys | `Float`                                  | relative radial velocity                                                        |
| zsource | `Float`                                  | the redshift of the source                                                      |
|  colnum | `Int`                                    | column of FITS binary table associated with this WCS                            |
| dateavg | `String`                                 | representative mid-point of the date of observation                             |
| dateobs | `String`                                 | start of the date of observation                                                |
| radesys | `String`                                 | the equatorial or ecliptic coordinate system type                               |
| specsys | `String`                                 | spectral reference frame (standard of rest)                                     |
| ssysobs | `String`                                 | spectral reference frame                                                        |
| ssyssrc | `String`                                 | spectral reference frame for redshift                                           |
| wcsname | `String`                                 | name of this coordinate representation                                          |
|  obsgeo | `Vector{Float}[3]` or `Vector{Float}[6]` | location of the observer in a standard terrestrial reference frame              |
|     alt | `String`                                 | character code for alternate coordinate descriptions                            |
