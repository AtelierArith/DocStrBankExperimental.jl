```
randtransmat([rng,] prior) -> Matrix{Float64}
```

Generate a transition matrix where each row is sampled from `prior`.   The prior must be a multivariate probability distribution, such as a Dirichlet distribution.

**Arguments**

  * `prior::MultivariateDistribution`: distribution over the transition matrix rows.

**Example**

```julia
A = randtransmat(Dirichlet([0.1, 0.1, 0.1]))
```
