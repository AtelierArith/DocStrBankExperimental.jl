```
DiscreteNonParametric(xs, ps)
```

A *Discrete nonparametric distribution* explicitly defines an arbitrary probability mass function in terms of a list of real support values and their corresponding probabilities

```julia
d = DiscreteNonParametric(xs, ps)

params(d)  # Get the parameters, i.e. (xs, ps)
support(d) # Get a sorted AbstractVector describing the support (xs) of the distribution
probs(d)   # Get a Vector of the probabilities (ps) associated with the support
```

External links

  * [Probability mass function on Wikipedia](http://en.wikipedia.org/wiki/Probability_mass_function)
