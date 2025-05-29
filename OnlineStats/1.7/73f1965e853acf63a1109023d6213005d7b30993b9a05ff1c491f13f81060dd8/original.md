```
FastForest(p, nkeys=2; stat=FitNormal(), kw...)
```

Calculate a random forest where each variable is summarized by `stat`.

# Keyword Arguments

  * `nt=100`: Number of trees in the forest
  * `b=floor(Int, sqrt(p))`: Number of random features for each tree to receive
  * `maxsize=1000`: Maximum size for any tree in the forest
  * `splitsize=5000`: Number of observations in any given node before splitting
  * `λ = 5 * (1 / nt)`: Probability that each tree is updated on a new observation

# Example

```
x, y = randn(10^5, 10), rand(1:2, 10^5)

o = fit!(FastForest(10), zip(eachrow(x),y))

classify(o, x[1,:])
```
