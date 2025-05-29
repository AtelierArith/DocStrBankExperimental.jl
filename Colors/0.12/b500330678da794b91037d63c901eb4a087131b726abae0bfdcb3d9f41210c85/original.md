```
colormatch(wavelength)
colormatch(matchingfunction, wavelength)
```

Evaluate the CIE standard observer color match function.

# Arguments

  * `matchingfunction` (optional): a type used to specify the matching function. Choices include:

      * `CIE1931_CMF` (the default, the CIE 1931 2° matching function)
      * `CIE1964_CMF` (the CIE 1964 10° color matching function)
      * `CIE1931J_CMF` (Judd adjustment to `CIE1931_CMF`)
      * `CIE1931JV_CMF` (Judd-Vos adjustment to `CIE1931_CMF`)
      * `CIE2006_2_CMF` (transformed from the CIE 2006 2° LMS cone fundamentals)
      * `CIE2006_10_CMF` (transformed from the CIE 2006 10° LMS cone fundamentals)
  * `wavelength`: Wavelength of stimulus in nanometers.

Returns the XYZ value of perceived color.

!!! note
    As of February 2020, only `CIE1931_CMF` and `CIE1964_CMF` have been standardized by the ISO/CIE. `CIE2006_2_CMF` and `CIE2006_10_CMF` are proposals which have yet to be ratified by the CIE, even though they are sometimes referred to as CIE 2012 CMFs.

