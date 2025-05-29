```
ismeuv(wave, hcol[, he1col=hcol*0.1, he2col=0, fano=false]) -> tau
```

### Purpose

Compute the continuum interstellar EUV optical depth

### Explanation

The EUV optical depth is computed from the photoionization of hydrogen and helium.

### Arguments

  * `wave`: wavelength value (in Angstroms). Useful range is 40 - 912 A; at shorter wavelength metal opacity should be considered, at longer wavelengths there is no photoionization.
  * `hcol`: interstellar hydrogen column density in cm-2.
  * `he1col` (optional): neutral helium column density in cm-2. Default is 0.1*hcol (10% of hydrogen column)
  * `he2col` (optional): ionized helium column density in cm-2 Default is 0.
  * `fano` (optional boolean keyword): If this keyword is true, then the 4 strongest auto-ionizing resonances of He I are included. The shape of these resonances is given by a Fano profile - see Rumph, Bowyer, & Vennes 1994, AJ, 107, 2108. If these resonances are included then the input wavelength vector should have a fine (>~0.01 A) grid between 190 A and 210 A, since the resonances are very narrow.

### Output

  * `tau`: Vector giving resulting optical depth, non-negative values.

### Example

One has a model EUV spectrum with wavelength, w (in Angstroms). Find the EUV optical depth by 1e18 cm-2 of HI, with N(HeI)/N(HI) = N(HeII)/N(HI) = 0.05.

```jldoctest
julia> using AstroLib

julia> ismeuv.([670, 910], 1e19, 5e17, 5e17)
2-element Vector{Float64}:
 27.35393320556168
 62.683796028917286
```

### Notes

Code of this function is based on IDL Astronomy User's Library.
