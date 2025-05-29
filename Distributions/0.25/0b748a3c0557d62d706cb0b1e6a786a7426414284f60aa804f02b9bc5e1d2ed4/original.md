```
Categorical(p)
```

A *Categorical distribution* is parameterized by a probability vector `p` (of length `K`).

$$
P(X = k) = p[k]  \quad \text{for } k = 1, 2, \ldots, K.
$$

```julia
Categorical(p)   # Categorical distribution with probability vector p
params(d)        # Get the parameters, i.e. (p,)
probs(d)         # Get the probability vector, i.e. p
ncategories(d)   # Get the number of categories, i.e. K
```

Here, `p` must be a real vector, of which all components are nonnegative and sum to one.

**Note:** The input vector `p` is directly used as a field of the constructed distribution, without being copied.

`Categorical` is simply a type alias describing a special case of a `DiscreteNonParametric` distribution, so non-specialized methods defined for `DiscreteNonParametric` apply to `Categorical` as well.

External links:

  * [Categorical distribution on Wikipedia](http://en.wikipedia.org/wiki/Categorical_distribution)
