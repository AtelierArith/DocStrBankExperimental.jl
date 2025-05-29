```
orbital_angular_velocity_to_semimajor_axis(angvel::Number, e::Number, i::Number; kwargs...) -> T, Bool
```

Compute the semi-major axis [m] that will provide an angular velocity `angvel` [rad / s] in an orbit with eccentricity `e` and inclination `i` [rad].

Notice that the angular velocity `angvel` is related to the nodal period, *i.e.* the time between two consecutive passages by the ascending node.

!!! note
    The output type `T` in the first signature is obtained by promoting the inputs to a float type.


# Keywords

  * `max_iterations::Int`: Maximum number of iterations allowed in the Newton-Raphson   algorithm.   (**Default** = 20)
  * `perturbation::Symbol`: Symbol to select the perturbation terms that will be used.   (**Default**: `:J2`)
  * `tolerance::Union{Nothing, Number}`: Residue tolerances to verify if the numerical method   has converged. If it is `nothing`, `√eps(T)` will be used, where `T` is the internal   type for the computations. Notice that the residue function unit is [deg / min].   (**Default** = nothing)
  * `m0::Number`: Standard gravitational parameter for Earth [m³ / s²].   (**Default** = `GM_EARTH`)
  * `J2::Number`: J₂ perturbation term.   (**Default** = `EGM_2008_J2`)
  * `J4::Number`: J₄ perturbation term.   (**Default** = `EGM_2008_J4`)
  * `R0::Number`: Earth's equatorial radius [m].   (**Default** = `EARTH_EQUATORIAL_RADIUS`)

# Returns

  * `T`: Semi-major axis [m].
  * `Bool`: `true` if the numerical method converged, `false` otherwise.

# Perturbations

The keyword argument `perturbation` can be used to select the perturbation terms that will be considered in the computation. The possible values are:

  * `:J0`: Consider a Keplerian orbit.
  * `:J2`: Consider the perturbation terms up to J2.
  * `:J4`: Consider the perturbation terms J2, J4, and J2².

If `perturbation` is omitted, it defaults to `:J2`.
