```
sor_efficiency(cut; F, D, Oc, pol=:matched, dz=0.0) -> (;ηₗₒₛₛ, ηₛₚ, ηᵢₗ, ηₚₕ, ηₚₒₗ, ηₓ)
```

Compute boresight directivity efficiency of a parabolic single-offset reflector using the feed pattern specified by `cut`.

## Positional input arguments:

  * `cut`: Either a string containing the name of a Ticra-compatible, spherical, polar, asymmetric cut file, or a `Cut` object as returned by the `read_cutfile` function.

## Keyword input arguments:

  * `F`, `D`, and `Oc`:  The single-offset reflector focal length, aperture diameter, and center offset, respectively.  These may be expressed in any convenient length units, so  long as they are consistent.
  * `pol`: A `Symbol` having one of the values `:L3h`, `:L3v`, `:RHCP`, `:LHCP`, or :max (any variations in terms of capitalization are acceptable).  The first two denote Ludwig 3  horizontal (x) and vertical (y) polarizations, the second two denote the two senses of  circular polarization, and `:max` (the default) uses the polarization among the 4 previously listed that that has the maximum field amplitude.  Polarization efficiency and boresight polarization mismatch of the **secondary** pattern will be computed relative to the polarization specified by  this argument.  Note that for CP, this will be orthogonal to the *primary* copol.
  * `dz`: This is a signed distance along the zfeed direction, measured in wavelengths. It allows for repositioning the feed in an attempt to locate the feed phase center at the reflector focal point. Suppose that the feed's phase center is located 0.42 wavelengths inside the horn aperture. The horn origin should ideally be positioned closer to the reflector, so a positive value `dz = 0.42` would be specified to indicate that the horn has been repositioned in this manner.

## Return value:  A `NamedTuple` with the following fields:

;ηₗₒₛₛ, ηₛₚ, ηᵢₗ, ηₚₕ, ηₚₒₗ, ηₓ

  * `ηₗₒₛₛ`: Feed loss efficiency (ratio of radiated power to 4π).
  * `ηₛₚ`: Spillover efficiency (a real number between 0 and 1).
  * `ηᵢₗ`: Illumination (amplitude taper) efficiency (a real number between 0 and 1).
  * `ηₚₕ`:  Phase error efficiency (a real number between 0 and 1).
  * `ηₚₒₗ`: Polarization efficiency (a real number between 0 and 1).
  * `ηₓ`: Boresight polarization mismatch loss efficiency (a real number between 0 and 1)
