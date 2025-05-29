MaxwellBoltzmannParticle(     dir::ParticleDirection,     part::AbstractParticleType,     temperature::Real )

マクスウェル・ボルツマン粒子分布は、単一粒子分布であり、四元運動量の空間成分が位置 $\mu = 0$ および分散 $\sigma = m k_B T$ で正規分布しています（$m$ は粒子の質量、$k_B$ はボルツマン定数、$T$ は温度です）。生成された粒子状態の三次元大きさ $\varrho = \sqrt{p_x^2 + p_y^2 + p_z^2}$ は [`MaxwellBoltzmann`](@ref) 分布に従います。

外部リンク

  * [ウィキペディアのマクスウェル・ボルツマン分布に関するページ](https://en.wikipedia.org/wiki/Maxwell–Boltzmann_distribution#Distribution_for_the_momentum_vector)
