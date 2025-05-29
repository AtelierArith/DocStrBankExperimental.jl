```
Geometric(p)
```

A *Geometric distribution* characterizes the number of failures before the first success in a sequence of independent Bernoulli trials with success rate `p`.

$$
P(X = k) = p (1 - p)^k, \quad \text{for } k = 0, 1, 2, \ldots.
$$

```julia
Geometric()    # Geometric distribution with success rate 0.5
Geometric(p)   # Geometric distribution with success rate p

params(d)      # Get the parameters, i.e. (p,)
succprob(d)    # Get the success rate, i.e. p
failprob(d)    # Get the failure rate, i.e. 1 - p
```

External links

  * [Geometric distribution on Wikipedia](http://en.wikipedia.org/wiki/Geometric_distribution)
