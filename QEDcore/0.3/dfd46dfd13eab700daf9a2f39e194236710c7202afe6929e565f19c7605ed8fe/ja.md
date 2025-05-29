```
ParticleStateful <: AbstractParticle
```

状態を持つ粒子の表現。4つのフィールドがあります：

  * `dir::ParticleDirection`: 粒子の方向、`Incoming()` または `Outgoing()`。
  * `species::AbstractParticleType`: 粒子の種、`Electron()`、`Positron()` など。
  * `mom::AbstractFourMomentum`: 粒子の運動量。

`is_fermion`、`is_boson`、`is_particle`、`is_anti_particle`、`is_incoming`、`is_outgoing`、`mass`、および `charge` のオーバーロードが提供されており、呼び出しを正しいフィールドに委譲することで `AbstractParticle` インターフェースを実装しています。

```jldoctest
julia> using QEDcore

julia> ParticleStateful(Incoming(), Electron(), SFourMomentum(1, 0, 0, 0))
ParticleStateful: incoming electron
    momentum: [1.0, 0.0, 0.0, 0.0]

julia> ParticleStateful(Outgoing(), Photon(), SFourMomentum(1, 0, 0, 0))
ParticleStateful: outgoing photon
    momentum: [1.0, 0.0, 0.0, 0.0]
```
