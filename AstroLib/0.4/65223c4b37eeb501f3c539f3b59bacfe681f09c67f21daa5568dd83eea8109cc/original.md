```
mag2flux(mag[, zero_point, ABwave=number]) -> flux
```

### Purpose

Convert from magnitudes to flux expressed in erg/(s cm² Å).

### Explanation

This is the reverse of `flux2mag`.

### Arguments

  * `mag`: the magnitude to be converted in flux.
  * `zero_point`: the zero point level of the magnitude.  If not supplied then defaults to 21.1 (Code et al 1976).  Ignored if the `ABwave` keyword is supplied
  * `ABwave` (optional numeric keyword): wavelength, in Angstroms.  If supplied, then the input `mag` is assumed to contain Oke AB magnitudes (Oke & Gunn 1983, ApJ, 266, 713; http://adsabs.harvard.edu/abs/1983ApJ...266..713O).

### Output

The flux.

If the `ABwave` keyword is set, then the flux is given by the expression

$$
\text{flux} = 10^{-0.4(\text{mag} +2.406 + 4\log_{10}(\text{ABwave}))}
$$

Otherwise the flux is given by

$$
\text{flux} =  10^{-0.4(\text{mag} + \text{zero point})}
$$

### Example

```jldoctest
julia> using AstroLib

julia> mag2flux(8.3)
1.7378008287493692e-12

julia> mag2flux(8.3, 12)
7.58577575029182e-9

julia> mag2flux(8.3, ABwave=12)
3.624411568301719e-7
```

### Notes

Code of this function is based on IDL Astronomy User's Library.
