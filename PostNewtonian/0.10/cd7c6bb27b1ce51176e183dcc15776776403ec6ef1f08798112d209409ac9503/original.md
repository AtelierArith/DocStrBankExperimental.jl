```
𝓔(pnsystem)
binding_energy(pnsystem)
```

Compute the gravitational binding energy of a compact binary.

Note that this may not be as useful as its derivative, [`𝓔′`](@ref), which is used as part of the right-hand side for orbital evolutions.

The nonspinning orbital binding energy is known through 4pN.  The expressions through 3.5pN here come from Eq. (233) of [Blanchet (2014)](https://doi.org/10.12942/lrr-2014-2).

The 4pN term from Eq. (5.2d) of [Jaranowski and Schäfer](https://arxiv.org/abs/1303.3225v1) is known exactly, now that the $ν$-linear piece is given as Eq. (32) of [Bini and Damour (2013a)](https://arxiv.org/abs/1305.4884v1).  The remaining terms are not known exactly, but [Bini and Damour (2013b)](https://arxiv.org/abs/1312.2503v2) have derived some terms, though there is incomplete information, which are noted as the constants in this code.

The spin-orbit terms in the energy are now complete to 4.0pN (the last term is zero).  These terms come from Eq. (4.6) of [Bohé et al. (2012)](https://arxiv.org/abs/1212.5520v2).

The spin-squared terms (by which we mean both spin-spin and spin-orbit squared terms) in the energy are known to 3pN order, and given in Eq. (3.33) of [Bohé et al. (2015)](https://arxiv.org/abs/1501.01529).

The tidal-coupling terms come in to the binding energy at relative 5pN order, and are known to 6pN order.  These terms come from Eq. (2.11) of [Vines et al. (2011)](https://prd.aps.org/abstract/PRD/v83/i8/e084051).  Note their unusual convention for mass ratios, where $χ₁ = m₁/m$ in their notation; in particular, $χ$ is not a spin parameter.  Also note that $λ̂ = λ₂ v^{10}/(m₁+m₂)^5$, and we need to add the coupling terms again with $1 ↔ 2$.  Finally, note the normalization difference, where a different overall factor is used, leading to a sign difference.
