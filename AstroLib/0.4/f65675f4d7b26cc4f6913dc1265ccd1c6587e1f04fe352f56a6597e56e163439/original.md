```
imf(mass, expon, mass_range) -> psi
```

### Purpose

Compute an N-component power-law logarithmic initial mass function (IMF).

### Explanation

The function is normalized so that the total mass distribution equals one solar mass.

### Arguments

  * `mass`: mass in units of solar mass, vector.
  * `expon`: power law exponent, vector. The number of values in expon equals the number of different power-law components in the IMF.
  * `mass_range`: vector containing the mass upper and lower limits of the IMF and masses where the IMF exponent changes. The number of values in mass*range should be one more than in expon. The values in mass*range should be monotonically increasing and positive.

### Output

  * `psi`: mass function, number of stars per unit logarithmic mass interval evaluated for supplied masses.

### Example

Show the number of stars per unit mass interval at 3 Msun for a Salpeter (expon = -1.35) IMF, with a mass range from 0.1 MSun to 110 Msun.

```jldoctest
julia> using AstroLib

julia> imf([3], [-1.35], [0.1, 110]) / 3
1-element Vector{Float64}:
 0.01294143518151214
```

### Notes

Code of this function is based on IDL Astronomy User's Library.
