```
PoissonBinomial(p)
```

A *Poisson-binomial distribution* describes the number of successes in a sequence of independent trials, wherein each trial has a different success rate. It is parameterized by a vector `p` (of length $K$), where $K$ is the total number of trials and `p[i]` corresponds to the probability of success of the `i`th trial.

$$
P(X = k) = \sum\limits_{A\in F_k} \prod\limits_{i\in A} p[i] \prod\limits_{j\in A^c} (1-p[j]), \quad \text{ for } k = 0,1,2,\ldots,K,
$$

where $F_k$ is the set of all subsets of $k$ integers that can be selected from $\{1,2,3,...,K\}$.

```julia
PoissonBinomial(p)   # Poisson Binomial distribution with success rate vector p

params(d)            # Get the parameters, i.e. (p,)
succprob(d)          # Get the vector of success rates, i.e. p
failprob(d)          # Get the vector of failure rates, i.e. 1-p
```

External links:

  * [Poisson-binomial distribution on Wikipedia](http://en.wikipedia.org/wiki/Poisson_binomial_distribution)
