```
AbstractParticleStateful <: QEDbase.AbstractParticle
```

状態を持つ粒子の表現のための抽象基本型です。次のインターフェース関数を提供する必要があります：

  * [`particle_direction`](@ref): 粒子の方向を返します。
  * [`particle_species`](@ref): 粒子の種を返します。
  * [`momentum`](@ref): 粒子の運動量を返します。

[`is_fermion`](@ref)、[`is_boson`](@ref)、[`is_particle`](@ref)、[`is_anti_particle`](@ref)、[`is_incoming`](@ref)、[`is_outgoing`](@ref)、[`mass`](@ref)、および[`charge`](@ref)の実装は、上記のインターフェース関数を使用して自動的に提供され、[`QEDbase.AbstractParticle`](@ref)インターフェースを満たします。
