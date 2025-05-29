```julia
struct Ball2D{P, V, A, M, I<:Integer} <: PhysicalParticles.AbstractParticle2D
```

  * `Pos::PhysicalParticles.PVector2D{P} where P`
  * `Vel::PhysicalParticles.PVector2D{V} where V`
  * `Acc::PhysicalParticles.PVector2D{A} where A`
  * `Mass::Any`
  * `ID::Integer`

基本的な2D粒子タイプ。

## 例

```jl
julia> Ball2D()
Ball 0: Pos = PVector2D{Float64}(0.0, 0.0), Vel = PVector2D{Float64}(0.0, 0.0), Acc = PVector2D{Float64}(0.0, 0.0), Mass = 0.0

julia> Ball2D(uAstro)
Ball 0: Pos = PVector2D(0.0 kpc, 0.0 kpc), Vel = PVector2D(0.0 kpc Gyr^-1, 0.0 kpc Gyr^-1), Acc = PVector2D(0.0 kpc Gyr^-2, 0.0 kpc Gyr^-2), Mass = 0.0 M⊙

julia> Ball2D(uSI, id = 1)
Ball 1: Pos = PVector2D(0.0 m, 0.0 m), Vel = PVector2D(0.0 m s^-1, 0.0 m s^-1), Acc = PVector2D(0.0 m s^-2, 0.0 m s^-2), Mass = 0.0 kg
```
