```
helio_rv(jd, T, P, V_0, K[, e, ω]) -> rv
```

### Purpose

Return the heliocentric radial velocity of a spectroscopic binary.

### Explanation

This function will return the heliocentric radial velocity of a spectroscopic binary star at a given heliocentric date given its orbit.

### Arguments

  * `jd`: time of observation, as number of Julian days.
  * `T`: time of periastron passage (max. +ve velocity for circular orbits), same time system as `jd`
  * `P`: the orbital period in same units as `jd`
  * `V_0`: systemic velocity
  * `K`: velocity semi-amplitude in the same units as `V_0`
  * `e`: eccentricity of the orbit.  It defaults to 0 if omitted
  * `ω`: longitude of periastron in degrees.  It defaults to 0 if omitted

### Output

The predicted heliocentric radial velocity in the same units as Gamma for the date(s) specified by `jd`.

### Example

  * What was the heliocentric radial velocity of the primary component of HU Tau at 1730 UT 25 Oct 1994?

    ```jldoctest
    julia> using AstroLib

    julia> jd = juldate(94, 10, 25, 17, 30); # Obtain Geocentric Julian days

    julia> hjd = helio_jd(jd, ten(04, 38, 16) * 15, ten(20, 41, 05)); # Convert to HJD

    julia> helio_rv(hjd, 46487.5303, 2.0563056, -6, 59.3)
    -62.965570107789475
    ```

    NB: the functions `juldate` and `helio_jd` return a reduced HJD (HJD - 2400000) and so T and P must be specified in the same fashion.
  * Plot two cycles of an eccentric orbit, $e = 0.6$, $ω = 45°$ for both components of a binary star.  Use [Plots.jl](https://github.com/JuliaPlots/Plots.jl) for plotting.

    ```julia
    using Plots
    φ = range(0, stop=2, length=1000); # Generate 1000 phase points
    plot(φ, helio_rv.(φ, 0, 1, 0, 100, 0.6, 45)) # Plot 1st component
    plot(φ, helio_rv.(φ, 0, 1, 0, 100, 0.6, 45+180)) # Plot 2nd component
    ```

### Notes

The user should ensure consistency with all time systems being used (i.e. `jd` and `t` should be in the same units and time system).  Generally, users should reduce large time values by subtracting a large constant offset, which may improve numerical accuracy.

If using the the function `juldate` and `helio_jd`, the reduced HJD time system must be used throughtout.

Code of this function is based on IDL Astronomy User's Library.
