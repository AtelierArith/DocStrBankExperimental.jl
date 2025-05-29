```julia
struct Massless2D{P, V, I<:Integer} <: PhysicalParticles.AbstractParticle2D
```

  * `Pos::PhysicalParticles.PVector2D{P} where P`
  * `Vel::PhysicalParticles.PVector2D{V} where V`
  * `ID::Integer`

質量のない2D粒子タイプ。

## 例

```jl
julia> Massless2D()
Massless 0: Pos = PVector2D{Float64}(0.0, 0.0), Vel = PVector2D{Float64}(0.0, 0.0)

julia> Massless2D(uAstro)
Massless 0: Pos = PVector2D(0.0 kpc, 0.0 kpc), Vel = PVector2D(0.0 kpc Gyr^-1, 0.0 kpc Gyr^-1)

julia> Massless2D(uSI, id = 1)
Massless 1: Pos = PVector2D(0.0 m, 0.0 m), Vel = PVector2D(0.0 m s^-1, 0.0 m s^-1)
```
