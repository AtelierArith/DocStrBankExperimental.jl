```julia
struct Ball{P, V, A, M, I<:Integer} <: PhysicalParticles.AbstractParticle3D
```

  * `Pos::PhysicalParticles.PVector{P} where P`
  * `Vel::PhysicalParticles.PVector{V} where V`
  * `Acc::PhysicalParticles.PVector{A} where A`
  * `Mass::Any`
  * `ID::Integer`

基本的な3D粒子タイプ。

## 例

```jl
julia> Ball()
Ball 0: Pos = PVector{Float64}(0.0, 0.0, 0.0), Vel = PVector{Float64}(0.0, 0.0, 0.0), Acc = PVector{Float64}(0.0, 0.0, 0.0), Mass = 0.0

julia> Ball(uAstro)
Ball 0: Pos = PVector(0.0 kpc, 0.0 kpc, 0.0 kpc), Vel = PVector(0.0 kpc Gyr^-1, 0.0 kpc Gyr^-1, 0.0 kpc Gyr^-1), Acc = PVector(0.0 kpc Gyr^-2, 0.0 kpc Gyr^-2, 0.0 kpc Gyr^-2), Mass = 0.0 M⊙

julia> Ball(uSI, id = 1)
Ball 1: Pos = PVector(0.0 m, 0.0 m, 0.0 m), Vel = PVector(0.0 m s^-1, 0.0 m s^-1, 0.0 m s^-1), Acc = PVector(0.0 m s^-2, 0.0 m s^-2, 0.0 m s^-2), Mass = 0.0 kg
```
