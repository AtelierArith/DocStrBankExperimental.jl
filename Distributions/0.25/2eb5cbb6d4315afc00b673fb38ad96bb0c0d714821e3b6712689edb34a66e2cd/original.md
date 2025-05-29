```
DiscreteUniform(a,b)
```

A *Discrete uniform distribution* is a uniform distribution over a consecutive sequence of integers between `a` and `b`, inclusive.

$$
P(X = k) = 1 / (b - a + 1) \quad \text{for } k = a, a+1, \ldots, b.
$$

```julia
DiscreteUniform(a, b)   # a uniform distribution over {a, a+1, ..., b}

params(d)       # Get the parameters, i.e. (a, b)
span(d)         # Get the span of the support, i.e. (b - a + 1)
probval(d)      # Get the probability value, i.e. 1 / (b - a + 1)
minimum(d)      # Return a
maximum(d)      # Return b
```

External links

  * [Discrete uniform distribution on Wikipedia](http://en.wikipedia.org/wiki/Uniform_distribution_(discrete))
