```
TransportPropertyData(prop, T, p, ϱ, η, phase=:unknown)
ViscosityData(T, p, ϱ, η, phase=:unknown)
ThermalConductivityData(T, p, ϱ, λ, phase=:unknown)
SelfDiffusionCoefficientData(T, p, ϱ, D, phase=:unknown)
InfDiffusionCoefficientData(T, p, ϱ, D, phase=:unknown)
```

Constructor for `TransportPropertyData`. Either pressure `p` or density `ϱ` have to be specified. `phase` can also be a `Vector{Symbol}`.

## Units

  * `[T] = K`
  * `[p] = Pa`
  * `[ϱ] = mol m⁻³`
  * `[η] = Pa s`
  * `[λ] = W (m K)⁻¹`
  * `[D] = m² s⁻¹`
