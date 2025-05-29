MaxwellBoltzmannParticle(     dir::ParticleDirection,     part::AbstractParticleType,     temperature::Real )

The Maxwell-Boltzmann particle distribution is a single-particle distribution, where the spatial components of the four-momentum are normally distributed with localion $\mu = 0$ and variance $\sigma = m k_B T$ ($m$ is the particle's mass, $k_B$ is the Boltzmann constant, and $T$ is the temperature). The three-magnitude $\varrho = \sqrt{p_x^2 + p_y^2 + p_z^2}$ of the generated particle-statefuls is [`MaxwellBoltzmann`](@ref) distributed.

External links

  * [Maxwell-Boltzmann distributed four-momenta on Wikipedia](https://en.wikipedia.org/wiki/Maxwell–Boltzmann_distribution#Distribution_for_the_momentum_vector)
