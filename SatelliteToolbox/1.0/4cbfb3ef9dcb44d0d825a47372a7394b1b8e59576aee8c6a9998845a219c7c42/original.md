```
orbital_period(a::Number, e::Number, i::Number; kwargs...) -> T
orbital_period(orb::Orbit{Tepoch, T}; kwargs...) where {Tepoch<:Number, T<:Number} -> T
```

Compute the orbital period [s] of an object in an orbit with semi-major axis `a` [m], eccentricity `e`, and inclination `i` [rad]. The orbit can also be specified by `orb` (see `Orbit`).

!!! note
    The output type `T` in the first signature is obtained by promoting the inputs to a float type.


# Keywords

  * `perturbation::Symbol`: Symbol to select the perturbation terms that will be used.   (**Default**: `:J2`)
  * `m0::Number`: Standard gravitational parameter for Earth [m³ / s²].   (**Default** = `GM_EARTH`)
  * `J2::Number`: J₂ perturbation term.   (**Default** = `EGM_2008_J2`)
  * `J4::Number`: J₄ perturbation term.   (**Default** = `EGM_2008_J4`)
  * `R0::Number`: Earth's equatorial radius [m].   (**Default** = `EARTH_EQUATORIAL_RADIUS`)

# Perturbations

The keyword argument `perturbation` can be used to select the perturbation terms that will be considered in the computation. The possible values are:

  * `:J0`: Consider a Keplerian orbit.
  * `:J2`: Consider the perturbation terms up to J2.
  * `:J4`: Consider the perturbation terms J2, J4, and J2².

If `perturbation` is omitted, it defaults to `:J2`.
