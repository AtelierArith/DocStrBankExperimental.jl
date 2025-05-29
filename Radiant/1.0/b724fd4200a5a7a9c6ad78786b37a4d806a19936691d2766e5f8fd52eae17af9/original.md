```
Surface_Source
```

Structure used to define a directionnal boundary source and its properties.

# Mandatory field(s)

  * `name::String` : name (or identifier) of the Surface_Source structure.
  * `particle::Particle` : type of particle emitted.
  * `energy_group::Int64` : energy group index in which the particle are emitted.
  * `direction::Vector{Float64}` : direction cosine.
  * `location::String` : boundary at which the source is located.
  * `boundaries::Vector{Float64}` : boundaries of the source along each axis [in cm].

# Optional field(s) - with default values

  * `intensity::Float64=1.0` : intensity [# particles/cm⁽ᴺ⁻¹⁾, where N is the geometry dimension].
