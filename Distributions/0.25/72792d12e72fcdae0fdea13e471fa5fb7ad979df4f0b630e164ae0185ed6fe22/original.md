```
Hypergeometric(s, f, n)
```

A *Hypergeometric distribution* describes the number of successes in `n` draws without replacement from a finite population containing `s` successes and `f` failures.

$$
P(X = k) = {{{s \choose k} {f \choose {n-k}}}\over {s+f \choose n}}, \quad \text{for } k = \max(0, n - f), \ldots, \min(n, s).
$$

```julia
Hypergeometric(s, f, n)  # Hypergeometric distribution for a population with
                         # s successes and f failures, and a sequence of n trials.

params(d)       # Get the parameters, i.e. (s, f, n)
```

External links

  * [Hypergeometric distribution on Wikipedia](http://en.wikipedia.org/wiki/Hypergeometric_distribution)
