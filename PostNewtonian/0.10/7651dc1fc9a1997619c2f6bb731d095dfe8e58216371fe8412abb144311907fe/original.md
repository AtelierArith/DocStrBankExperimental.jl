```
𝓕(pnsystem)
gw_energy_flux(pnsystem)
```

Compute the gravitational-wave energy flux to infinity

The nonspinning flux terms are complete to 4.5pN order, and are given in Eq. (6.11) of [Blanchet et al. (2023)](https://arxiv.org/abs/2304.11186).

The spin-orbit terms in the flux are now known to 4.0pN.  These terms come from Eq. (4.9) of [Marsat et al. (2013)](https://arxiv.org/abs/1307.6793v1)

The spin-squared terms (by which we mean both spin-spin and spin-orbit squared terms) in the flux are known to 3pN order, and given most conveniently in Eq. (4.14) of [Bohé et al. (2015)](https://arxiv.org/abs/1501.01529).

Beyond 4.5pN, terms are only known in the extreme-mass-ratio limit.  These terms are given in Appendix A of [Fujita (2012)](https://arxiv.org/abs/1211.5535v1).  He computed them up to 22pN.  That seems like overkill, so we'll just go up to 6pN.

For systems with matter, the tidal-heating terms come in at relative 5pN order, and are known partially at 6pN order.  These terms come from Eq. (3.6) of [Vines et al. (2011)](https://prd.aps.org/abstract/PRD/v83/i8/e084051).  Note their unusual convention for mass ratios, where $χ₁ = m₁/m$ in their notation; in particular, $χ$ is not a spin parameter.  Also note that $λ̂ = λ₂ v^{10}/(m₁+m₂)^5$, and we need to add the coupling terms again with $1 ↔ 2$.  Finally, note the normalization difference, where a different overall factor is used, leading to a sign difference.
