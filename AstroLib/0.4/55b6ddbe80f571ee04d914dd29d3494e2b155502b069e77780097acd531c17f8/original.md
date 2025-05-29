```
rhotheta(period, periastron, eccentricity, semimajor_axis, inclination, omega, omega2, epoch) -> rho, theta
```

### Purpose

Calculate the separation and position angle of a binary star.

### Explanation

This function will return the separation $ρ$ and position angle $θ$ of a visual binary star derived from its orbital elements.  The algorithms described in the following book will be used: Meeus J., 1992, Astronomische Algorithmen, Barth.  Compared to the examples given at page 400 and no discrepancy found.

### Arguments

  * `period`: period [year]
  * `periastro`: time of periastron passage [year]
  * `eccentricity`: eccentricity of the orbit
  * `semimajor_axis`: semi-major axis [arc second]
  * `inclination`: inclination angle [degree]
  * `omega`: node [degree]
  * `omega2`: longitude of periastron [degree]
  * `epoch`: epoch of observation [year]

All input parameters have to be scalars.

### Output

The 2-tuple $(ρ, θ)$, where

  * $ρ$ is separation [arc second], and
  * $θ$ is position angle (degree).

### Example

Find the position of Eta Coronae Borealis at the epoch 2016

```jldoctest
julia> using AstroLib

julia> ρ, θ = rhotheta(41.623, 1934.008, 0.2763, 0.907, 59.025, 23.717, 219.907, 2016)
(0.6351167848659552, 214.42513387396497)
```

### Notes

Code of this function is based on IDL Astronomy User's Library.
