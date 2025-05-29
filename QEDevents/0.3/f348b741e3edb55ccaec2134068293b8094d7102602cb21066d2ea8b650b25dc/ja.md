```
SingleParticleDistribution
```

単一粒子分布からサンプルを描画するための基本型。以下のインターフェース関数を実装する必要があります：

  * [`QEDevents._particle(d::SingleParticleDistribution)`](@ref): 関連する粒子を返す
  * [`QEDevents._particle_direction(d::SingleParticleDistribution)`](@ref): 関連する粒子の方向を返す
  * [`QEDevents._randmom(d::SingleParticleDistribution)`](@ref): `d` に従って運動量を返す
