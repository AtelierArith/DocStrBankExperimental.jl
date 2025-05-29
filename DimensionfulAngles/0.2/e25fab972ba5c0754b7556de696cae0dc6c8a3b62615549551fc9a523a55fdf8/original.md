```
Periodic()
```

Equivalence to convert between temporal or spatial period, frequency, [angular frequency](https://en.wikipedia.org/wiki/Angular_frequency), and angular period.

These quantities are related by $f = ω/2π = 1/T = 1/(2πT̅)$, where

  * $f$ is the (temporal) frequency,
  * $ω$ is the (temporal) angular frequency,
  * $T$ is the (temporal) period,
  * $T̄$ is the (temporal) angular period,

and $ν = k/2π = 1/λ = 1/(2πλ̄)$, where

  * $ν$ is the (spatial) frequency (linear wavenumber),
  * $k$ is the (spatial) angular frequency (angular wavenumber),
  * $λ$ is the (spatial) period (linear wavelength), and
  * $λ̄$ is the (spatial) angular period (angular wavelength).

See also [`DimensionfulAngles.Dispersion`](@ref)

# Example

```jldoctest; filter = r"(\d*).(\d{1,10})\d+" => s"\1.\2"
julia> using Unitful

julia> using DimensionfulAngles

julia> uconvert(u"s", 10u"Hz", Periodic())
0.1 s

julia> uconvert(u"radᵃ/s", 1u"Hz", Periodic())
6.283185307179586 rad s⁻¹
```
