```
airtovac(wave_air) -> wave_vacuum
```

### Purpose

Converts air wavelengths to vacuum wavelengths.

### Explanation

Wavelengths are corrected for the index of refraction of air under standard conditions. Wavelength values below $2000 Å$ will *not* be altered, take care within $[1 Å, 2000 Å]$.  Uses relation of Ciddor (1996).

### Arguments

  * `wave_air`: the wavelength in air.

### Output

Vacuum wavelength in angstroms.

### Method

Uses relation of Ciddor (1996), Applied Optics 62, 958.

### Example

If the air wavelength is `w = 6056.125` (a Krypton line), then `airtovac(w)` yields a vacuum wavelength of `6057.8019`.

```jldoctest
julia> using AstroLib

julia> airtovac(6056.125)
6057.801930991426
```

### Notes

`vactoair` converts vacuum wavelengths to air wavelengths.

Code of this function is based on IDL Astronomy User's Library.
