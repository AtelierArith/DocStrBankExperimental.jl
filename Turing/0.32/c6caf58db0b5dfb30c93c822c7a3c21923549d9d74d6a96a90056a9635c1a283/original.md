```
LogPoisson(logλ)
```

The *Poisson distribution* with logarithmic parameterization of the rate parameter describes the number of independent events occurring within a unit time interval, given the average rate of occurrence $exp(logλ)$.

The distribution has the probability mass function

$$
P(X = k) = \frac{e^{k \cdot logλ}{k!} e^{-e^{logλ}}, \quad \text{ for } k = 0,1,2,\ldots.
$$

See also: [`Poisson`](@ref)
