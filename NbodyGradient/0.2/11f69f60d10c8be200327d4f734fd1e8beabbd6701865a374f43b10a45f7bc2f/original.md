```
Elements{T<:AbstractFloat} <: AbstractInitialConditions
```

Orbital elements of a binary, and mass of a 'outer' body. See [Tutorials](@ref) for units and conventions.

# Fields

  * `m::T` : Mass of outer body.
  * `P::T` : Period [Days].
  * `t0::T` : Initial time of transit [Days].
  * `ecosω::T` : Eccentricity vector x-component (eccentricity times cosine of the argument of periastron)
  * `esinω::T` : Eccentricity vector y-component (eccentricity times sine of the argument of periastron)
  * `I::T` : Inclination, as measured from sky-plane [Radians].
  * `Ω::T` : Longitude of ascending node, as measured from +x-axis [Radians].
  * `a::T` : Orbital semi-major axis [AU].
  * `e::T` : Eccentricity.
  * `ω::T` : Argument of periastron [Radians].
  * `tp::T` : Time of periastron passage [Days].
