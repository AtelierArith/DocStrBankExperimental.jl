```
Skellam(μ1, μ2)
```

A *Skellam distribution* describes the difference between two independent [`Poisson`](@ref) variables, respectively with rate `μ1` and `μ2`.

$$
P(X = k) = e^{-(\mu_1 + \mu_2)} \left( \frac{\mu_1}{\mu_2} \right)^{k/2} I_k(2 \sqrt{\mu_1 \mu_2}) \quad \text{for integer } k
$$

where $I_k$ is the modified Bessel function of the first kind.

```julia
Skellam(μ1, μ2)     # Skellam distribution for the difference between two Poisson variables,
                    # respectively with expected values μ1 and μ2.

params(d)           # Get the parameters, i.e. (μ1, μ2)
```

External links:

  * [Skellam distribution on Wikipedia](http://en.wikipedia.org/wiki/Skellam_distribution)
