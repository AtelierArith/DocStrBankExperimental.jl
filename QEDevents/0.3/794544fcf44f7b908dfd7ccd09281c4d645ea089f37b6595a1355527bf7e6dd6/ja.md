MultiParticleDistribution

複数の粒子分布からサンプルを描画するための基本タイプ。以下のインターフェース関数を実装する必要があります：

  * [`QEDevents._particles(d::MultiParticleDistribution)`](@ref)
  * [`QEDevents._particle_directions(d::MultiParticleDistribution)`](@ref)
  * [`QEDevents._randmom(rng::AbstractRNG,d::MultiParticleDistribution)`](@ref)
