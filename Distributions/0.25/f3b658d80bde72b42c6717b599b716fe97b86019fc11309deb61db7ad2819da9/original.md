```
VonMises(μ, κ)
```

The *von Mises distribution* with mean `μ` and concentration `κ` has probability density function

$$
f(x; \mu, \kappa) = \frac{1}{2 \pi I_0(\kappa)} \exp \left( \kappa \cos (x - \mu) \right)
$$

```julia
VonMises()       # von Mises distribution with zero mean and unit concentration
VonMises(κ)      # von Mises distribution with zero mean and concentration κ
VonMises(μ, κ)   # von Mises distribution with mean μ and concentration κ
```

External links

  * [von Mises distribution on Wikipedia](http://en.wikipedia.org/wiki/Von_Mises_distribution)
