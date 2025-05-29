```julia
struct Massless{P, V, I<:Integer} <: PhysicalParticles.AbstractParticle3D
```

  * `Pos::PhysicalParticles.PVector{P} where P`
  * `Vel::PhysicalParticles.PVector{V} where V`
  * `ID::Integer`

3D particle type without mass.

## Examples

```jl
julia> Massless()
Massless 0: Pos = PVector{Float64}(0.0, 0.0, 0.0), Vel = PVector{Float64}(0.0, 0.0, 0.0)

julia> Massless(uAstro)
Massless 0: Pos = PVector(0.0 kpc, 0.0 kpc, 0.0 kpc), Vel = PVector(0.0 kpc Gyr^-1, 0.0 kpc Gyr^-1, 0.0 kpc Gyr^-1)

julia> Massless(uSI, id = 1)
Massless 1: Pos = PVector(0.0 m, 0.0 m, 0.0 m), Vel = PVector(0.0 m s^-1, 0.0 m s^-1, 0.0 m s^-1)
```
