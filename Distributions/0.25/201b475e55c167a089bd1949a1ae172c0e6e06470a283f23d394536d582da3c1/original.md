```
DirichletMultinomial
```

The [Dirichlet-multinomial distribution](https://en.wikipedia.org/wiki/Dirichlet-multinomial_distribution) is the distribution of a draw from a multinomial distribution where each sample has a  slightly different probability vector, drawn from a common Dirichlet distribution.

This contrasts with the multinomial distribution, which assumes that all observations arise from a single fixed probability vector. This enables the Dirichlet-multinomial distribution to accommodate more variable (a.k.a, over-dispersed) count data than the multinomial distribution.

The probability mass function is given by

$$
f(x; \alpha) = \frac{n! \Gamma(\alpha_0)}
{\Gamma(n+\alpha_0)}\prod_{k=1}^K\frac{\Gamma(x_{k}+\alpha_{k})}
{x_{k}! \Gamma(\alpha_{k})}
$$

where

  * $n = \sum_k x_k$
  * $\alpha_0 = \sum_k \alpha_k$

```julia
# Let α be a vector
DirichletMultinomial(n, α) # Dirichlet-multinomial distribution for n trials with parameter
vector α.

# Let k be a positive integer
DirichletMultinomial(n, k) # Dirichlet-multinomial distribution with n trials and parameter
vector of length k of ones.
```
