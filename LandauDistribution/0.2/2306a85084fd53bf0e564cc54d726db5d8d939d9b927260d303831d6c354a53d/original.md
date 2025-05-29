```
Landau(μ,θ)
```

The *Landau distribution* with location `μ` and scale `θ` has probability density function

$$
p(x) = \frac{1}{2 \pi i} \int_{\mu-i\infty}^{\mu+i\infty} e^{s \log(s) + x s}\, ds
$$

```julia
Landau()       # Landau distribution with zero location and unit scale, i.e. Landau(0, 1)
Landau(u)      # Landau distribution with location u and unit scale, i.e. Landau(u, 1)
Landau(u, b)   # Landau distribution with location u ans scale b

params(d)       # Get the parameters, i.e. (u, b)
location(d)     # Get the location parameter, i.e. u
scale(d)        # Get the scale parameter, i.e. b
```

External links

  * [Landau distribution on Wikipedia](http://en.wikipedia.org/wiki/Landau_distribution)
