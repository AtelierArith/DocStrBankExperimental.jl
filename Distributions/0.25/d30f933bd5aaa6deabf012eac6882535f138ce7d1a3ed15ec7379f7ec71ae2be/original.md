```
Poisson(λ)
```

A *Poisson distribution* describes the number of independent events occurring within a unit time interval, given the average rate of occurrence `λ`.

$$
P(X = k) = \frac{\lambda^k}{k!} e^{-\lambda}, \quad \text{ for } k = 0,1,2,\ldots.
$$

```julia
Poisson()        # Poisson distribution with rate parameter 1
Poisson(lambda)       # Poisson distribution with rate parameter lambda

params(d)        # Get the parameters, i.e. (λ,)
mean(d)          # Get the mean arrival rate, i.e. λ
```

External links:

  * [Poisson distribution on Wikipedia](http://en.wikipedia.org/wiki/Poisson_distribution)
