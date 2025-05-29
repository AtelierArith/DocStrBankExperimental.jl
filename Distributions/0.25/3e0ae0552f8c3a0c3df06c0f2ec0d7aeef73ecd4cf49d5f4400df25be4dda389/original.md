```
Laplace(μ,θ)
```

The *Laplace distribution* with location `μ` and scale `θ` has probability density function

$$
f(x; \mu, \theta) = \frac{1}{2 \theta} \exp \left(- \frac{|x - \mu|}{\theta} \right)
$$

```julia
Laplace()       # Laplace distribution with zero location and unit scale, i.e. Laplace(0, 1)
Laplace(μ)      # Laplace distribution with location μ and unit scale, i.e. Laplace(μ, 1)
Laplace(μ, θ)   # Laplace distribution with location μ and scale θ

params(d)       # Get the parameters, i.e., (μ, θ)
location(d)     # Get the location parameter, i.e. μ
scale(d)        # Get the scale parameter, i.e. θ
```

External links

  * [Laplace distribution on Wikipedia](http://en.wikipedia.org/wiki/Laplace_distribution)
