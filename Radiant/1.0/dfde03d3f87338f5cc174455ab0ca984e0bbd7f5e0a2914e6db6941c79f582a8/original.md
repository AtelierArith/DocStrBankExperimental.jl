```
Volume_Source
```

Structure used to define an isotropic volume source and its properties.

# Mandatory field(s)

  * `name::String` : name (or identifier) of the Volume_Source structure.
  * `particle::Particle` : type of particle emitted.
  * `energy_group::Int64` : energy group index in which the particle are emitted.
  * `boundaries::Vector{Float64}` : boundaries of the source along each axis [in cm].

# Optional field(s) - with default values

  * `intensity::Float64=1.0` : intensity [# particles/cmᴺ, where N is the geometry dimension].
