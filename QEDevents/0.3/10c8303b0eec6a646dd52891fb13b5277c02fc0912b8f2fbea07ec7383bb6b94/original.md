```
MaxwellBoltzmann(scale::Real)
```

The *Maxwell-Boltzmann distribution* with scale parameter `a` has the probability density function

$$
f(x,a) = \sqrt{\frac{2}{\pi}}\frac{x^2}{a^3}\exp\left(\frac{-x^2}{2a^2}\right)
$$

The Maxwell-Boltzmann distribution is related to the `Chi` distribution via the property $X\sim \operatorname{MaxwellBoltzmann}(a=1)$, then $X\sim\chi(\mathrm{dof}=3)$.

External links

  * [Maxwell-Boltzmann distribution on Wikipedia](https://en.wikipedia.org/wiki/Maxwell–Boltzmann_distribution)
  * [Maxwell-Boltzmann distribution on Wolfram MathWorld](https://mathworld.wolfram.com/MaxwellDistribution.html)
  * [Maxwell-Boltzmann distribution implementation in Scipy](https://docs.scipy.org/doc/scipy/reference/generated/scipy.stats.maxwell.html)
