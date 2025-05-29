```
κ₁(s)
```

The "quadrupolar polarisability" of object 1 used by [Bohé et al. (2015)](https://arxiv.org/abs/1501.01529).

Note that Bohé et al. refer to the closely related (and co-authored) [Marsat (2014)](https://arxiv.org/abs/1411.4118), who notes above Eq. (4.7) that this is denoted $C_{\mathrm{ES}^2}$ in [Levi and Steinhoff (2014)](https://arxiv.org/abs/1410.2601), who in turn notes that "we can set ... the Wilson coefficients $C_{\mathrm{ES}^2} = C_{\mathrm{BS}^3} = 1$ for the black hole case."

However, a very similar constant $\kappa_A$ is used in Eq. (2.1) of [Buonanno et al. (2012)](https://arxiv.org/abs/1209.6349).  They say that $\kappa_A=1$ for an *isolated* black hole, but can deviate from 1 for a black hole in a binary — though those deviations occur at "much higher" order than those they consider (2PN).

See also [`λ₁`](@ref).

!!! warn
    This function will be incorrect for objects other than black holes.  It is not clear to me if this is the same quantity as $C_Q$ used in some papers, such as [Bini and Geralico (2014)](https://arxiv.org/abs/1408.5261), but they point out that for neutron stars, the value varies between 4.3 and 7.4, depending on the equation of state.  This quantity may also be related to [`λ₁`](@ref).  Pull requests or issues with more information are welcome.

